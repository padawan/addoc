+++
url = "/marketplace/joomla/"
title = "Joomla"
layout = "man"
hidden = true
tags = [ "cms" ]
+++

## Common Issues

### Error ERR_CONTENT_DECODING_FAILED on static files

The _Gzip Page Compression_ option is incompatible with our default Apache configuration, which loads **already** compression on the fly. To correct, simply remove the last section of the `.htaccess` file from the root of the site.
