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
- [Case 1: add PEB minutes](#case-1-add-peb-minutes)
- [Case 2: submit a deliverable to the EC](#case-2-submit-a-deliverable-to-the-ec)
- [Case 3: achieve a milestone](#case-3-achieve-a-milestone)
- [Case 4: update a progress report](#case-4-update-a-progress-report)

### Case 1: add PEB minutes
##### Preliminary steps (off GitHub)
1. Copy [this google doc](https://docs.google.com/document/d/1PNlm7MWv1eHb7e7t6RaeyhlqH4hoEj4hFN1593BIgvI/edit?usp=sharing) in a new doc of your own, to have editing rights.
2. Overwrite it with the minutes from the newest PEB - _no need to keep native copy of all minutes_.
3. Send the link to your google doc in suggesting mode to `peb at expands.eu` for review.
4. Wait 24 hours.
5. Take comments into account.
6. Download final google minutes as .pdf, add the date of the meeting to the filename and upload it to `Sharepoint > General > Meetings > Project Executive Boards` - _this is your safe storage for auditing purposes_.

##### Back to GitHub
1. In `/_pebs`, duplicate `template.html`.
2. Rename it with date of the meeting in standard format `YYYY-MM-DD-notes.html`.
3. Remove first line `published: false`.
4. Update list of first name of attendees - _it is public so we avoid full names_.
5. In `intro:`, copy from the google doc whatever is before the "Status quo per WP" chapter. Use `<h2>` if you have several topics, further down is not defined in css.
6. In `status-quo:`, [as you can see from the template](/_layouts/peb_template.html), it's a list, so `status-quo[0]` (what comes after first hyphen) will go into the WP1 sub-chapter, `status-quo[1]` into the WP2 chapter, etc. You need to copy from the google doc each chapter into the corresponding list item.
7. in `aob:`, copy from the google doc whatever is after the "Status quo per WP" chapter. You can also add appendixes here. You'll find examples in the previous minutes (e.g. [2021-09-28](/_pebs/2021-09-28-notes.html)).

##### Tips
- Beware to __stay between the `""`__ of the template, e.g. `intro: "..."`, even if your text is super long. Careful with links or quotes in text: if there is a `"` somewhere, you'll need to escape it or use `'` instead. Jekyll will complain if you miss one.
- Be as true to the original format as possible, especially __bold__ words `<b>` and [links](https://expands.eu) `<a href=''>` otherwise the rendering is really boring.
- Be clean and use html tags everywhere, even if it manages without.
- __Don't delete any front matter property__, even if there is nothing to report in a WP or in the whole `status-quo:`, or even in `aob:`. Just leave it empty as in the template. 
- You'll notice the __"Actions / ToDo Items" table is not included__ in the public reporting page. This is because they are quickly obsolete. Be sure to keep them in the living google doc as long as they are ongoing though, so you can monitor them. _You can send a copy of the oen actions table in the e-mail to the PEB with the agenda for next meeting._
- You may also notice you've only changed the __front matter__ (that is what is between the two `---`) in your `YYYY-MM-DD-notes.html` file. That is supposed to be the case, so no worries. See Jekyll doc if you are curious.
- If there is a new PEB member, you can update the `template.html` file to include her/him in the default list of attendees.

### Case 2: submit a deliverable to the EC
##### Preliminary steps (off GitHub)
1. The author copies the [ExPaNDS doc template](https://docs.google.com/document/d/1nW4xydpOZUslvcsYOJtiEMn63qqb3_DGCPXVOIe_c_A/edit?usp=sharing) in a new doc of his own.
2. The deliverable is written and reviewed.
2. You or the author reserves a DOI in Zenodo and includes in the deliverable, following [these good practices](https://github.com/ExPaNDS-eu/ExPaNDS/wiki/ExPaNDS-community-in-Zenodo:-good-practices).
3. Once the document is reviewed internally and finalised, the author uploads .pdf and native version (or google doc link) in `Sharepoint > Deliverables`.
4. You or the author uploads the .pdf version of the document in Zenodo and publish it. Careful, you need to add in the `Additional notes` a __disclaimer__ that it is not yet approved by the EC (see [ExPaNDS issue #28](https://github.com/ExPaNDS-eu/ExPaNDS/issues/28) and [Zenodo good pratices for ExPaNDS](https://github.com/ExPaNDS-eu/ExPaNDS/wiki/ExPaNDS-community-in-Zenodo:-good-practices)). 
2. You upload the .pdf version of the deliverable in the EC portal.
2. You update the `Deliverables.xslx` table in `Sharepoint > Deliverables`.

##### Back to GitHub
1. In `/_data` open [`deliverables.yml`](/_data/deliverables.yml).
2. Look for your deliverable, `id` being the deliverable number.
3. Add its `doi` or if it has another PID type, add it using `link`.
4. Update the `date` if needed to fit with the actual delivery date to the EC.
5. Update the `status` to `delivered`.
6. Add a `description`. Try to keep the same tone and length as the other deliverables' descriptions, that is: short and standalone.

##### Tips
- When a deliverable is accepted by the Commission, you can remove the disclaimer in Zenodo and change its `status` in [`deliverables.yml`](./_data/deliverables.yml) to `accepted`.

### Case 3: achieve a milestone
##### Preliminary steps (off GitHub)
1. Once a milestone is considered achieved, upload any necessary justification material to `SharePoint > Milestones`. Can be in Zenodo too if relevant ([see example here](https://expands-eu.github.io/WP1-reporting/milestones.html)).
2. Agree on a __short justification text__ with the WP leader of this milestone for the Commission.
2. Tick the milestone box in the __EC portal__ and include the above justification in the comments box. 
3. Update the `Milestones.xlsx` table in `Sharepoint > Milestones`.

##### Back to GitHub
1. In `/data_` open [`milestones.yml`](/_data/milestones.yml).
2. Look for your milestone using the `id`. 
4. Update the `date` if needed to fit with the actual achievement date.
5. Update the `status` to `achieved`.
6. Add in `comments` the justification, exactly as it was entered in the EC portal.
3. (optional) Add its `doi` or if it has another PID type, add it using `link`.

### Case 4: update a progress report
##### Preliminary steps (off GitHub)
1. Have a dedicated WP meeting with one WP leader, her/his co-leader, her/his deputy if applicable, the technical coordinator and the project coordinator.
2. Copy the corresponding google doc ([WP1](https://docs.google.com/document/d/1ymU246DcV1b7D9SysG118XGTWjb5eRahYDYaJJqn0qw/edit), [WP2](https://docs.google.com/document/d/1pWi4GbYhTpfsG038g0I5cnNIL0jsPoNsBZ8CHPsFZ7Q/edit), [WP3](https://docs.google.com/document/d/1LSIUyphkwdMb93nT-nkdXmvyD3_EfRTnjTR7W99iVEE/edit), [WP4](https://docs.google.com/document/d/1RsJoziami1WjDf_W1jTJYTJ6lzjfFyCUzyAGxGraKQ0/edit), [WP5](https://docs.google.com/document/d/1rIGVZwXJCvXCmAUqb4BXQRrirgz-68Gt2IQuKmIsOWw/edit) or [WP6](https://docs.google.com/document/d/1CiaAajO8MTKt4gA1-wZXjETutNLp0SfytGkGDWuP4Ow/edit)) in a new doc of your own, to have editing rights.
2. Take minutes in your google doc and agree on final text with participants.

##### Back to GitHub
1. In `/_reports`, duplicate [`template.html`](/_reports/template.html).
2. Rename it with date of the meeting and WP in standard format `YYYY-MM-DD-WPx.html`.
3. Remove first line `published: false`.
4. Fill in WP number in `wp: "x"`
6. In `progress:`, [as you can see from the template](/_layouts/report_wp_template.html), it's a list, so `progress[0]` (what comes after first hyphen) will go into the task 1 sub-section, `progress[1]` into the task 2 section, etc. You need to copy from the google doc each progress section of each task into the corresponding list item.
7. Same with `next-steps:`, copy from the google doc each next steps section of each task into the corresponding list item. If a next steps section is empty for a task, leave the list item emtpy.
8. And that's it, check the rendering looks good and push to master.
