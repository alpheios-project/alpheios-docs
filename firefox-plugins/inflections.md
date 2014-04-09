The Alpheios Greek inflection table data can be found at

https://svn.code.sf.net/p/alpheios/code/inflections/grc/trunk/src/

These XML files are the source data for both the Inflection Tables display in the Alpheios Greek Firefox Plugin and the Alpheios Inflection Quiz display.

Runtime XSLT transformations are found in

https://svn.code.sf.net/p/alpheios/code/xml_ctl_files/xslt/trunk/

The relevant files are all named alph-infl-* or alph-verb-*

http://alpheios.net/content/alpheios-firefox-plugins#codemap

If you want an overview of the full functionality set available for the Alpheios inflection tables (which include matching morpheus output to a specific inflection ending, verb paradigm, etc.) take a look at the [Alpheios test plan document](tests/alpheiostestplanpdf). There are some very detailed tests on the inflection matching which should give you a sense of what is currently covered. You can also look at the public documentation available in the user guide on the alpheios.net site.

The majority of the Alpheios Inflection display and quiz functionality is implemented via the XSLT transformations with Javascript driver code for the transformations (which includes setting of the input parameters to the XSLT transforms) and display.  The javascript driver code for the Greek is found in

https://svn.code.sf.net/p/alpheios/code/language-extensions/greek/trunk/content/alpheios-greek-langtool.js

there are 3 relevant methods:

Alph.LanguageTool_Greek.prototype.getInflectionTable = function(a_node, a_params, a_checkonly)

Alph.LanguageTool_Greek.setInflectionXSL = function(a_params,a_infl_type,a_form)

Alph.LanguageTool_Greek.prototype.handleInflectionDisplay = function(a_tbl,a_str,a_params)

If you want to follow how this works at runtime, you can inspect the HTML contents of the Alpheios morphology popup (i.e. with Firebug or the Firefox web development tools).  In the above-referenced javascript code you will see references to HTML element classes like alph-dict, alph-pofs, etc. These all are found in the Alpheios popup, and come directly from the morpheus output (as represented per the Alpheios lexicon schema (https://svn.code.sf.net/p/alpheios/code/xml_ctl_files/schemas/trunk/lexicon.xsd) and transformed via https://svn.code.sf.net/p/alpheios/code/xml_ctl_files/xslt/trunk/alpheios.xsl . 
