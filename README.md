# GrahamIELTS documents

Live site: https://documents.grahamielts.workers.dev
Cloudflare Worker `documents`, deployed from this repository on every push to `main`.

## Layout

    /                 a plain landing card, no student names, nothing to browse
    /builder/         the report builder, sign-in required, me only
    /<student>/       one folder per student, one index.html inside it

## Making a report for a student

1. Open https://documents.grahamielts.workers.dev/builder/ and sign in with Cloudflare.
   The offline copy, Downloads\GrahamIELTS-Report-Builder.html, works too.
2. Fill in the form. The report builds live on the right.
3. Download index.html.
4. Open https://github.com/GrahamIELTS/documents/upload/main/STUDENTNAME
   That link creates the folder as part of the upload. The builder prints the exact
   link for whatever name you have typed.
5. Drag index.html on and press Commit changes.
6. A minute later it is live at
   https://documents.grahamielts.workers.dev/STUDENTNAME/

## Who can see what

Student reports are public to anyone holding the link and set to noindex, so search
engines skip them. The root page lists nothing, so one student's link never leads to
another's.

The builder is not public. A Cloudflare Access application sits in front of
/builder/ and only gman292@gmail.com gets through. It is managed under
Zero Trust, Access controls, Applications, "GrahamIELTS Report Builder".

Nothing typed into the builder is sent anywhere. It stays in the browser.
