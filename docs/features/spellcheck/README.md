---
category: working-with-document
order: 20
url: features/spellcheck
menu-title: Spelling and Grammar Checking
meta-title-short: Spell Checking
---
<!--
Copyright (c) 2003-2021, CKSource - Frederico Knabben. All rights reserved.
For licensing, see LICENSE.md.
-->

# Proofreading, Spelling and Grammar Checking

<info-box info="">
    The out-of-the-box spelling and grammar checking functionality is provided through plugins that are included in the Standard and Full presets available from the official CKEditor 4 <a href="https://ckeditor.com/ckeditor-4/download/">Download</a> site. You can also {@link guide/dev/plugins/README add them to your custom build} with <a href="https://ckeditor.com/cke4/builder">online builder</a>.
</info-box>

CKEditor 4 can be configured to use either native spell checking capabilities provided by the browser or to use an external spell checking web service.

## Native Browser Spell Checker

By default, native browser spell check functionality is disabled in the editor. Use the {@linkapi CKEDITOR.config.disableNativeSpellChecker `config.disableNativeSpellChecker`} configuration option to enable it:

```js
config.disableNativeSpellChecker = false;
```

After reloading the editor you should be able to see the spelling corrections underlined in your editor content.

**Note**: If the [Context Menu](https://ckeditor.com/cke4/addon/contextmenu) plugin is enabled, it is necessary to hold the <kbd>Ctrl</kbd> key when right-clicking misspelled words to see their suggestions.

**Note**: The spell check functionality is not available natively for all browsers.

## Spell Check As You Type (SCAYT)

The [SpellCheckAsYouType (SCAYT)](https://ckeditor.com/cke4/addon/scayt) plugin provides inline spelling and grammar checking, much like the native browser spell checker, well-integrated with the CKEditor 4 context menu.

It is provided by [WebSpellChecker](https://webspellchecker.com/wsc-scayt-ckeditor4/). It uses the WebSpellChecker web services, transferring the text to their servers and performing spelling and grammar checking. This is a cross-browser solution.

{@img assets/img/scayt_02.png 876 Spell Check As You Type in CKEditor 4 WYSIWYG editor}

## Spell Checking in a Dialog Window

<info-box warning="">
	**This feature has an End-of-Life date set to December 31st, 2021.** This means it will not be supported any longer and may stop working after this date. We strongly encourage everyone to choose one of the other available spellchecking solutions - {@link features/spellcheck/README#spell-check-as-you-type-scayt Spell Check As You Type (SCAYT)} or {@link features/spellcheck/README#distraction-free-proofreading WProofreader}.
</info-box>

The [WebSpellChecker Dialog](https://ckeditor.com/cke4/addon/wsc) plugin is another spell checker solution provided by [WebSpellChecker](https://webspellchecker.com/wsc-dialog-ckeditor4/). It runs the check through a dialog window instead of marking misspelled words inline. Additionally, for some languages a Grammar Checker and Thesaurus feature is also available.

{@img assets/img/wsc_01.png 881 Spell Checker in the dialog window in CKEditor 4 WYSIWYG editor}

## Distraction-free Proofreading

<info-box info="">
    This is a commercial solution provided by our partner, [WebSpellChecker](https://webspellchecker.com/). You can report any issues in its [GitHub repository](https://github.com/WebSpellChecker/wproofreader).
</info-box>

[WProofreader](https://webspellchecker.com/wsc-proofreader) is an innovative proofreading tool that combines the functionality of "spell check as you type" and "spell check in a dialog" in a modern UI. Spelling, punctuation and grammar suggestions are available on hover with no clicking needed or as a convenient dialog, both with additional in-place replacement suggestions.

{@img assets/img/wproofreader_01.png 730 Spelling and grammar checking with WProofreader in CKEditor 4 WYSIWYG editor}

The proofreader badge in the bottom-right corner shows you the total number of mistakes detected. Hover an underlined word to display the proofreader suggestions for any of the spelling and grammar mistakes found. This hovercard allows the user to employ the feature on the go.


{@img assets/img/wproofreader_02.png 730 Distraction-free proofreader badge in CKEditor 4 WYSIWYG editor}

If you want to see an overview of all spelling and grammar mistakes, click the "Proofread in dialog" icon in the badge. It will invoke a detached floating panel, easy to navigate and perfect for dedicated proofreading sessions. Turning it on brings a dialog similar to the on-hover one, but substantially larger. It is a detached, floating window that can be conveniently moved around as needed, which is especially important on small screens. However, it also supports accessibility, as moving it left may be more convenient for left-handed persons or more comfortable in the case of right-to-left languages.

{@img assets/img/wproofreader_03.png 776 Proofreading dialog in CKEditor 4 WYSIWYG editor}

In order to use the proofreader, you need to add a few lines of configuration to your editor:

```js
window.WEBSPELLCHECKER_CONFIG = {
    autoSearch: true,
    enableGrammar: true,
    serviceId: 'your-service-ID'
};
```

And load the following script on your site:

```html
<script type="text/javascript" src="https://svc.webspellchecker.net/spellcheck31/wscbundle/wscbundle.js"></script>
```

WProofreader is a commercial solution, so you need to [purchase a license](https://ckeditor.com/contact/) and then add your `serviceId` to the configuration. You can also [request a free trial ID](https://ckeditor.com/contact/).

Additionally, this feature is bundled with the [SCAYT](https://ckeditor.com/cke4/addon/scayt) and [WebSpellChecker Dialog](https://ckeditor.com/cke4/addon/wsc) plugins, so you can use it as long as you have WSC or SCAYT installed.

For more detailed documentation, refer to the [official WProofreader "Getting Started" guide](https://docs.webspellchecker.net/pages/viewpage.action?pageId=442663877).

## Supported Languages

### Language support

The most popular languages offered by WebSpellChecker solutions include: American English, British English, Canadian English, Canadian French, French, German, Italian, Greek, Spanish, Finnish, Danish, Dutch, Portuguese, Swedish, Ukrainian, Norwegian Bokmål, Brazilian Portuguese. There are, however, over 160 languages altogether, available for download from the WebSpellChecker site. Grammar checking is available for over 20 languages.

A recent addition to the software are AI-driven tools. Smart algorithms employed in the AI-based language dictionaries offer a far better checking quality, generating proofreading suggestions based on the context of the sentence. They provide more suitable suggestions that address mistakes with thrice the accuracy of traditional dictionaries. The AI-based support is currently available for English and German.

Here you can check the [full list of available languages](https://webspellchecker.com/additional-dictionaries/).

### Custom dictionaries

Apart from the language dictionaries, WebSpellChecker offers two specialized dictionaries: a **medical** and a **legal** one, available for an additional fee.

There are also two types of custom dictionaries available.

One is the **user dictionary** that can be expanded and will grow during the regular use of the feature simply by adding new words to the dictionary. This is a perfect solution for editors and writers working on specific content that may contain slang or professional jargon.

The other is the so-called **company-wide dictionary**. These premade dictionaries can be uploaded by the system administrators or CKEditor 5 integrators and can be made available company-wide, accessible for all users. This way all benefits of a user-generated dictionary can be shared among the team, making the proofreading process more structured and controlled.

### Multi-language Support

If you have content in multiple languages, the spell check feature can automatically detect the text language properly. It is enough to choose “Auto Detect” in the Language dropdown of the spell checker settings. Suggestions for spelling and grammar (where available) will be displayed properly for each text fragment.

{@img assets/img/wproofreader_04.png 771 Choose the auto-detect language option.}

## Customization Options

The SCAYT and WebSpellChecker plugins include numerous configuration options that let you customize the default spell checking language, the number of SCAYT suggestions available or the content of the spell checker context menu and dialog window.

You can find them on the {@linkapi CKEDITOR.config `CKEDITOR.config`} API page, starting from `scayt_` and `wsc_`.

<info-box hint="">
    The out-of-the-box spell checking functionality of SCAYT and WebSpellChecker Dialog is ad-supported. If you want to remove the ads, you can <a href="https://ckeditor.com/contact/">purchase a license here</a>.
</info-box>

## Spell Checking Demo

See the {@linkexample spellchecker working "Proofreading, Spelling and Grammar Checking" sample} that showcases all three official spell and grammar checking solutions.
