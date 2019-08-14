---
layout: post
title: A Quick Guide to OmegaT
featured: true
tags: [Localization]
---

# A QUICK GUIDE TO OMEGAT

## OVERVIEW

tbd

## HOW TO INSTALL OMEGAT IN YOUR LOCAL MACHINE

tbd

## HOW TO TRANSLATE USING OMEGAT

tbd

## HOW TO USE TRANSLATION MEMORY AND WHY

tbd

## HOW TO USE GLOSSARY AND WHY

tbd

## HOW TO USE MACHINE TRANSLATIONS

### How to install Microsoft Translator

You can install Microsoft Translator into OmegaT and fetch the machine translation automatically. Use the shortcuts of Ctrl/Command+M to fill the segment with the machine translation.

The following instructions are based on OmegaT 4.1.5. For the older and later versions, the configurations may be different. Please refer to the **User's Manual**.

### 1. Azure Account

You need an Azure Account to subscribe to the Microsoft Translator in Microsoft Azure Marketplace. OmegaT needs the subscription key to utilize Microsoft Translator.

1. Access the Translator Text page on  [Microsoft Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.CognitiveServicesTextTranslation?tab=Overview ). If the link is invalid, please search the Microsoft Azure Marketplace for the right page.
2. Sign in with your account or create a new account following the registration steps.

- You may need a new account to access the free trial.

1. Subscribe to Microsoft Translator Text and pick the pricing tier of F0.

- F0 provides machine translation of up to 2,000,000 characters per month for free, which is enough for AI Team translation job (for now).
- You can choose other tiers suitable for your need, which may require additional payment and credit card registration. 

*The details may change after certain updates in the user's interfaces or pricing strategies. If you encounter any problems, please contact IT before any uncertain configurations. * 

### 2. API key

After the subscription, you can generate the keys to activate Microsoft Translator in your OmegaT, following these steps:

1. Click the **Translator Service** in your **Azure Dashboard**.
2. Click **Resource Management** > **Keys**.
3. **Key 1** and **Key 2** will be generated automatically. 

- It may take a few minutes for the newly (re)generated keys to take effect.

### 3. Activate the plug-in

OmegaT needs your subscription key to implement the Mircosoft Translator. The configuration may be slightly different if you use a different version.

1. Click **Options** > **Preferences** > **Machine Translation** in your OmegaT.
2. Check the **Automatically fetch translations** box.
3. Choose **Microsoft Translator** in the Providers and then click **Configure**.
4. Paste your subscription key from Microsoft Translator into the corresponding blank.
5. Check the **Neural machine translation** box if you want to fetch the machine translation of NMT.

- You can check the details about **Neural Machine Translation** (NMT) and **Statistical Machine Translation** (SMT) in the [Microsoft Translator Documentation](https://docs.microsoft.com/zh-cn/azure/cognitive-services/translator/translator-info-overview). In short, NMT exceeds SMT in the translation quality, especially for Chinese and some other languages.

1. Click **Confirm**.

Now, you have utilized Microsoft Translator in your OmegaT. You can open a project and test the machine translation. 

- If you encounter any issues concerning the machine translation service, please contact IT or Microsoft Azure.

### 4. Usage limit

The Quota of 2,000,000 characters per month is sufficient for most personal projects and small/micro businesses. 

You can check your usage and the quota on your Microsoft Azure Dashboard by the following steps:

1. Click the **Cognitive Services** > **Overview** on your **Dashboard**.
2. Check the **Quota Info** on the bottom of the page.
3. The **Free tier include quantity Total** display your usage limit; the **Free tier include quantity Remaining** displays the quota left. 

Or you can view your detailed usage by hours by following steps:

1. Click the **Cognitive Services** > **Metrics** on your **Dashboard**.
2. Click **Add metric** and select the corresponding **Resource**, **Metric Namespace**, **Metric** (Characters Translated), **Aggregation** (Sum).
3. You can configure alerts for this metric by clicking **More** > **Configure alerts**. 
   - You need to pay for the automatic alerts. 

## HOW TO TRANSLATE XLSX FILE(S) IN OMEGAT

### Overview

The Open XML filter of OmegaT loads the .xlsx strings in the physical order in the source document instead of the logic order in the spreadsheet. In this case, you may find that the segments are ranked *randomly* in the OmegaT Editor, which would be confusing for you to track the segments and their context.

Refer to [OmegaT Bug Ticket #288 on SourceForge](https://sourceforge.net/p/omegat/bugs/288/) for the bug details.

As this issue hasn't been fixed yet, you can process your .xlsx file(s) to generate an "organized" intermediate file with Okapi Rainbow in following steps.

Okapi Framework is a free, open-source, cross-platforms and Java-based localization toolkit. You can download the package and read the documentation on its website [Okapi Framework.org](http://okapiframework.org/wiki/index.php?title=Main_Page).  You may need to install or upgrade Java on your local machine. 

Rainbow is a toolbox with GUI in the Okapi Framework.

### Steps

You need to pre-process, translate and then post-process the .xlsx files as follows:

#### 1. Pre-process .xlsx file(s) with Rainbow

1. Download Okapi Framework to your local machine and open Rainbow.
2. Drag your source .xlsx file(s) into the Input List.
3. Configure your customized rules if necessary. 
   1. Right-click the "okf-openxml" > **Edit Document Properties** or Double-click it to open **Input Document Properties** window.
   2. Click **Create** to create a new configuration for your .xlsx file(s).
   3. In **Office 2007 Filter Parameters** > **Excel Options**, configure as you need.
      - e.g. Check the box of **Translate Sheet Names** or select the columns or in different sheets you don't need to translate to exclude them from the intermediate file(s).
4. Set your language pair and the corresponding encodings in the tab of **Languages and Encodings**.
5. Set your root and path and folder rules in **Other Settings**. You can also use the default.
6. Click **Utilities** > **Translation Kit Creation** in the menu.
7. Select **Generic XLIFF** or **OmegaT Project** in the Type of package to create window.
   - If you already have a OmegaT project for this job, or the .xlsx files belongs to a bigger project consisting of more files, select **XLIFF.**
   - If it is a new or standalone job, select **OmegaT Project**. 
8. Click **Execute**.

#### 2. Load the intermediate file(s) into OmegaT and translate

If you select XLIFF, load the intermediate file(s) into OmegaT in following steps:

1. Go the same folder your .xlsx file(s) in by default settings or your customized output path.
2. Open the folder **pack1** (default) > **work** to find your intermediate file(s) whose extension name is **.xlf**.
3. Load the .xlf file(s) into OmegaT by moving the file(s) into the source folder in your existed OmegaT project folder, or by clicking **Project** > **Load Source File(s)** in the menu.
4. Start to translate.

If you select OmegaT project, load the project into OmegaT in following steps:

1. Click **Project** > **Open** in the menu.
2. Find your project folder in the default or your customized output path.
3. Click **Open**.

#### 3. Post-process and create the translated .xlsx file(s)

After the translation is done, you need to convert the file(s) back to .xlsx in following steps:

1. Click **Project** > **Create Translated Files** in the menu or use short-cut **Ctrl + Shift + D**.
2. Open Rainbow and drag the file **manifest.rkm** in pack1 into the Input List.
3. Click **Utilities** > **Translation Kit Post-processing** in the menu.
4. After the processing is done, you can find the translated .xlsx file(s) in **...\pack1\done**.

### Spreadsheet Notes

Be careful with the following issues when processing spreadsheets:

- Translating headers and sheet names may corrupt the calculation of formulas and functions.
  - e.g. vlookup.
- Convert the units when necessary. 
  - e.g. inches and meters/centimeters, dollars and RMB, etc.
- Heights and widths of the cells may need adjustments in the translated .xlsx file(s), especially for EN-ZH language pair.
- tbd

## HOW TO CONTACT OMEGAT

If you encounter any issues concerning OmegaT, please contact the developers by the following approaches:

1. [Yahoo Group](https://groups.yahoo.com/neo/groups/OmegaT/info) (recommended)

2. [SourceForge](https://sourceforge.net/projects/omegat/support)

   You can also get support from other OmegaT users on [Proz.com](https://www.proz.com/forum/omegat_support/).