WILLYCARTOONS — SITE BUNDLE (self-hosted fonts)
================================================

WHAT TO UPLOAD
--------------
Upload everything below to your web root, keeping this exact structure.
The paths in the HTML are relative, so the fonts/ folder must sit
alongside the HTML file.

    my_rep_optimized.html      <- rename to index.html if this is your homepage
    fonts.css
    logo-header.webp
    logo-full.webp
    logo-tile.webp
    fonts/
        inter-latin-400-normal.woff2
        inter-latin-500-normal.woff2
        inter-latin-600-normal.woff2
        inter-latin-700-normal.woff2
        inter-latin-ext-400-normal.woff2
        inter-latin-ext-500-normal.woff2
        inter-latin-ext-600-normal.woff2
        inter-latin-ext-700-normal.woff2
        inter-cyrillic-400-normal.woff2
        inter-cyrillic-500-normal.woff2
        inter-cyrillic-600-normal.woff2
        inter-cyrillic-700-normal.woff2
        space-grotesk-latin-600-normal.woff2
        space-grotesk-latin-700-normal.woff2
        space-grotesk-latin-ext-600-normal.woff2
        space-grotesk-latin-ext-700-normal.woff2
        LICENSE-Inter.txt
        LICENSE-SpaceGrotesk.txt


WHAT CHANGED
------------
The site no longer requests anything from Google Fonts. Both typefaces
are served from your own domain.

Only the subsets a visitor actually needs get downloaded:
    most languages ....... 7 files,  ~128 KB
    Russian .............. 10 files, ~151 KB
    (cached after the first page view)


RECOMMENDED SERVER SETTINGS
---------------------------
Fonts are immutable, so cache them hard. Add ONE of the following,
depending on your host.

Apache (.htaccess):

    <FilesMatch "\.woff2$">
      Header set Cache-Control "public, max-age=31536000, immutable"
    </FilesMatch>
    AddType font/woff2 .woff2

Nginx:

    location ~* \.woff2$ {
      add_header Cache-Control "public, max-age=31536000, immutable";
      types { font/woff2 woff2; }
    }

Netlify (_headers file):

    /fonts/*
      Cache-Control: public, max-age=31536000, immutable

Vercel (vercel.json):

    { "headers": [{
        "source": "/fonts/(.*)",
        "headers": [{ "key": "Cache-Control",
                      "value": "public, max-age=31536000, immutable" }]
      }] }

If your host serves the site from a different origin than the fonts
(a CDN, for example), the font files also need:

    Access-Control-Allow-Origin: *

Fonts are already compressed, so do NOT gzip or brotli .woff2 files.


CHECKING IT WORKED
------------------
Open the site, press F12 -> Network tab, filter by "Font", reload.
You should see .woff2 files coming from your own domain and nothing
from fonts.gstatic.com.


LICENSING
---------
Inter and Space Grotesk are both under the SIL Open Font License 1.1,
which permits self-hosting and commercial use. The license text is
included in fonts/ and must stay with the font files.
