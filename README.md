## Zotero translators 
### English Short Title Catalogue
Out of the box, <a href="http://zotero.org">Zotero</a> will ingest records from the English Short Title Catalogue quite happily, using the translator for Aleph library catalogues in conjunction with the MARC translator. The default behavior isn't especially well-suited for working with ESTC records, however. These translators make a few tweaks to improve things.

There are *two* javascript files here, which both need to be added to Zotero's collection of translators. `English Short Title Catalogue.js` notes when you're at the ESTC and directs Zotero to use the second file, `MARC-2.js` in place of the standard `MARC.js` translator. `MARC-2 .js`is just a slightly altered version of the standard `MARC.js` translator that:
* Grabs the ESTC citation number and places it in the "Extra" field.
* Grabs the entire, messy pagination statement (rather than just the first thing that looks like a number).
* Inclues citation notes (the MARC 510 field) in Zotero notes
* Separates multiple notes with a pipe character (`' | '`) for easier parsing later.

### American Antiquarian Society
Behaves like the English Short Title Catalogue translator, in that it gets the full pagination statement and all notes. The "Extra" field doesn't currently work, however (I'd need to spend some more time looking at AAS records to see what, if anything, should go there...).

### Short-Title Catalogue, Netherlands
Like the ESTC translators, this translator makes a few tweaks to the existing PICA translator to make the results that Zotero imports more friendly for book historical work:
* The STCN fingerprint goes in the "Extra" field.
* The imprint information gets split into city and publisher fields.
* The format and collation statement gets put into the number of pages field.
* Typographical information gets saved as a note.

These translators lean very, very heavily on the work of the original developers, Simon Kornblith, Sylvain Machefert, Michael Berkowitz, Ming Yeung Cheung, and Sebastian Karcher. Duplicating the work of the `MARC.js` module for the ESTC translator strikes me as a particularly inelegant kludge, but I take some comfort in seeing that that seems to be more or less the same approach that was used to adapt the Aleph translator to deal with quirks of one library's OPAC using the `MAB2.js` translator.

If you're unfamiliar with GitHub, you can download all the files in this repository as a .zip file using the link at the bottom of the left sidebar. Once you've downloaded and extracted the .zip file, you'll need to place the javascript files for the translator(s) you want to use where your copy of Zotero can find them. 

If you're using Mac OS X, these javascript files need to go in the folder located	 at `/Users/<your-username>/Zotero/translators/`. If you are using Zotero Standalone on Windows 10, the files go in `C:\\Users\<your-username>\Zotero\translators`. (These file paths have changed since I first put these together. They seem to be correct for Zotero 5.)
  
I've tested these translators on macOS and (less extensively) on Windows 10. They work for me with Zotero Standalone when using Safari and Chrome on the Mac, and with Zotero Standalone with Chrome on Windows 10. It can be a little fiddly getting Zotero to recognize that they're there. You might need to do some or all of the following: 
* In Zotero Standalone Preferences, under "Advanced," click on the button to update translators
* In your browser, refresh the page and/or empty browser cache
* In your browser, deactivate and reactivate the Zotero extension
* In your browser, deactivate *all* extensions and then reactivate them.
