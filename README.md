# [Unsanitize Safelinks](https://git.logicalhacking.com/adbrucker/unsanitize-safelinks): A Utility for Microsoft's Safelinks

Both the home and personal online offerings of Microsoft Outlook (e.g., Outlook.com, Office 365 Home,
or Office 365 Personal) and the professional Office 365 offerings (e.g., as part of Office 365 Advanced
Threat Detection) might rewrite links in received emails with the goal of protecting users against
certain treats (e.g., phishing).

For various reasons, one might to rewrite these `"safelinks" back into their original form. The script
[unsantize-safelinks](./unsantize-safelinks) does exactly this. This can, for example, be used for
displaying mails nicely in [mutt](https://www.mutt.org) or other text-based mail programs. In your 
".muttrc" you need to add/edit the following configuration:

```muttrc
set display_filter="unsanitize-safelinks"
```

If you want to also rewrite the links when using tools such as urlscan, use:

```muttrc
macro index,pager \cb "<pipe-message> unsanitize-safelinks| urlscan<Enter>"
```

And the following trick rewrites the links prior to editing a message (e.g., when replying):

```muttrc
set editor ="unsanitize-safelinks -i %s && $EDITOR %s"
```

Finally, if links should be rewritten when viewing the HTML-part, you need to edit your your ".mailcap"
entry for type "text/html":

```mailcap
text/html; unsanitize-safelinks -i --html %s && /usr/bin/sensible-browser %s; description=HTML Text; nametemplate=%s.html
```

## Author

* [Achim D. Brucker](http://www.brucker.ch/)

## License

This project is licensed under a 2-clause BSD license.

SPDX-License-Identifier: BSD-2-Clause

## Master Repository

The master git repository for this project is hosted
<https://git.logicalhacking.com/adbrucker/unsanitize-safelinks>.
