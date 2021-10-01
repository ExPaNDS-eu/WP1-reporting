WP1 openly reporting for the ExPaNDS project.
Page building at https://expands-eu.github.io/WP1-reporting/.

# Local builds
For local builds, you will need to install [Jekyll](https://jekyllrb.com/).
```
~ $ gem install bundler jekyll
~ $ git clone git@github.com:ExPaNDS-eu/WP1-reporting.git
~ $ cd WP1-reporting
~/WP1-reporting $ bundle exec jekyll serve
# now browse to http://localhost:4000 and tada
```
# Maintenance
Here all you need to know to maintain the site.

### Case 1: add PEB minutes
##### Preliminary steps (off GitHub)
1. Copy [this google doc](https://docs.google.com/document/d/1PNlm7MWv1eHb7e7t6RaeyhlqH4hoEj4hFN1593BIgvI/edit?usp=sharing) in a new doc of your own, to have editing rights.
2. Overwrite it with the minutes from the newest PEB - _no need to keep native copy of all minutes IMHO_.
3. Send the link to your google doc in suggesting mode to `peb at expands.eu` for review.
4. Wait 24 hours.
5. Take comments into account - _this will not happen too often_.
6. Download final google minutes as .pdf, add the date of the meeting to the filename and upload it to `Sharepoint > General > Meetings > Project Executive Boards` - _this is your safe storage for 10 years_.

##### Back to GitHub
1. In `/_pebs`, duplicate `template.html`.
2. Rename it with __date of the meeting__ in standard format `YYYY-MM-DD-notes.html`.
3. Remove first line `published: false`.
4. Update list of first name of attendees - _it is public so we prefer to avoid full names_.
5. In `intro:`, copy from the google doc whatever is __before__ the "Status quo per WP" chapter. Use `<h2>` if you have several topics, further down is not defined in css.
6. In `status-quo:`, [as you can see from the template](/_layouts/peb_template.html), it's a list, so `status-quo[0]` (what comes after first hyphen) will go into the WP1 sub-chapter, `status-quo[1]` into the WP2 chapter, etc. You need to copy from the google doc each chapter into the corresponding list item.
7. in `aob:`, copy from the google doc whatever is __after__ the "Status quo per WP" chapter. You can also add appendixes here. You'll find examples in the previous minutes (e.g. [2021-09-28](/_pebs/2021-09-28-notes.html)).

##### Tips
- Beware to __stay between the `""`__ of the template, e.g. `intro: "..."`, even if your text is super long. Careful with links or quotes in text: if there is a `"` somewhere, you'll need to use `'` instead. Jekyll will complain if you miss one.
- Be as true to the original format as possible, especially __bold__ words `<b>` and [links](https://expands.eu) `<a href=''>` otherwise the rendering is really boring.
- Be clean and use html tags everywhere, even if it manages without.
- __Don't delete any front matter property__, even if there is nothing to report in a WP or in the whole `status-quo:`, or even in `aob:`. Just leave it empty as in the template. 
- You'll notice the __"Actions / ToDo Items" table is not included__ in the public reporting page. This is because they are quickly obsolete so don't bother adding them. But be sure to keep them in the living google doc as long as they are ongoing, so you can monitor them. _You can also send a copy of the actions table in the e-mail to the PEB with the agenda for next meeting if you want._
- You may also notice you've only changed the __front matter__ (that is what is between the two `---`) in your `YYYY-MM-DD-notes.html` file. That is supposed to be the case, so no worries. See Jekyll doc if you are curious.
- If there is a new PEB member, you can update the `template.html` file to include her/him in the default list of attendees.

### Case 2: submit a deliverable to the EC
##### Preliminary steps (off GitHub)
1. The author copies the [ExPaNDS doc template](https://docs.google.com/document/d/1nW4xydpOZUslvcsYOJtiEMn63qqb3_DGCPXVOIe_c_A/edit?usp=sharing) in a new doc of his own.
2. The deliverable is written and reviewed.
2. You reserve a DOI in Zenodo and send it to the author to be included in the deliverable.
3. Once the document is reviewed internally and finalised, the author uploads .pdf and native version (or google doc link) in `Sharepoint > Deliverables`.
4. You upload the .pdf version of the document in Zenodo and publish it. _Note: uploading .pdf is not FAIR at all, we should upload both .pdf and .odt (TBD)._ Careful, you need to add in the `Additional notes` a __disclaimer__ that it is not yet approved by the EC (see [ExPaNDS issue #28](https://github.com/ExPaNDS-eu/ExPaNDS/issues/28)). 
2. You upload the .pdf version of the deliverable in the EC portal.
2. You update the `Deliverables.xslx` table in `Sharepoint > Deliverables`.

##### Back to GitHub
1. In `/_data` open `deliverables.yml`.
2. Look for your deliverable, `id` being the deliverable number.
3. Update its `link:` and `img:` properties using the links provided by Zenodo in `Target URL` and `Image URL`, respectively. Should be something like that:
```
  link: https://doi.org/10.5281/zenodo.xxxxxxx
  img: https://zenodo.org/badge/DOI/10.5281/zenodo.xxxxxxx.svg
```
4. Update the `date:` if needed to fit with the actual delivery date to the EC.
5. Update the `status: delivered`.
6. Add a `description`. Try to keep the same tone and length as the other deliverables' descriptions, that is: short and standalone.
