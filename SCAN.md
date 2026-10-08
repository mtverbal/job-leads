Daily job scan for Andy "Fish" McElfresh. It feeds the job-leads page at andymcelfresh.com/jobs/, which reads jobs.json from the GitHub repo mtverbal/job-leads. That repo should be cloned into this session's working directory. GitHub access comes from the connected GitHub account; there is no key, and none is needed.

THE ONE RULE THAT MATTERS MOST
Fish is using this list to apply for jobs he badly needs. A dead or fake listing wastes his time and his hope; a missing listing costs nothing. So: never add a job unless you have opened the employer's own posting (or its ATS API record) in this run and it shows the job open. If you can't confirm it, leave it out. Do not add "Unverified" jobs. Fewer, real leads beat a long list.

WHO FISH IS
LA-based senior writer-producer with wide-ranging writing across media: comedy/TV (2,400+ episodes of The Tonight Show with Jay Leno, co-creator of Rocket Power, writer on White Chicks), MTV/Nickelodeon/NBC, Marvel comics, podcasts, books. He writes the live pregame shows for NVIDIA GTC (San Jose, Taipei, Berlin): hosted broadcast countdown shows with panels, tape packages and host copy that stream before the CEO keynote. He does not write the keynote itself.
He has written press releases for Zagat, MTV and Fox TV Studios, so comms and PR-adjacent writing roles are in range, though he is not a media-relations specialist.
He has an integrated-marketing background: on MTV Beach House he turned advertisers' marketing goals into MTV programming (7-Eleven, Lee Jeans, Pepsi, McDonald's); McDonald's hired him to write its first animated McDonaldland show, which led to Rocket Power; and he started at The Tonight Show creating integrated segments for American Airlines. His through-line: making programming that does a marketing team's job and still gets watched.

WHAT HE WANTS
Writing, writer-producer and creative roles on live and streamed shows and events; exec-comms, keynote-content and event-content teams at tech companies; copy and creative leadership at experiential/event agencies; branded entertainment and integrated-marketing content; in-house content studios at consumer brands. Full-time, contract and freelance are all fine; remote, LA-based or travel-heavy are all fine. Not MasterClass.

Titles (corporate teams rarely say "writer"): show writer, head writer, scriptwriter, writer-producer, segment producer, creative producer (live events), keynote content producer, executive presentations writer, event content lead, narrative or content strategist (events), executive communications manager, brand storyteller, content producer, head of content, branded content / branded entertainment lead, integrated marketing creative, senior copywriter, associate creative director (copy), creative director, executive creative director.

Include exec-comms, keynote and comms-writing roles even when the posting mentions comms experience; say in the note how much PR/comms background it seems to want. Skip: pure media-relations/publicist roles, social-media-only, internal-comms-only, technical/AV engineering, staff jobs on scripted TV series.

SENIORITY: Only tag a job "fish" if it is senior: Senior, Lead, Principal, Head, Director, Executive Producer, Supervising, Creative Director, roughly 8+ years asked, or a freelance/contract writing gig where seniority doesn't apply. Associate, Coordinator, Junior, Assistant, Specialist and mid-level roles go to "all", never "fish".

HOW TO FIND AND CONFIRM JOBS
Step 1, employer boards (the main source; spend most of the run here). companies.md lists target companies. For each company, record its applicant-tracking system and board slug in companies.md the first time you find it (format: "Company | ats | slug-or-careers-URL"), so later runs can go straight to it. Read the boards directly, using WebFetch on these public JSON endpoints, which list every open job with real dates:
  - Greenhouse: https://boards-api.greenhouse.io/v1/boards/<slug>/jobs (one job, with first_published and the full description: .../jobs/<id>)
  - Lever: https://api.lever.co/v0/postings/<slug>?mode=json (createdAt is epoch milliseconds)
  - Ashby: https://api.ashbyhq.com/posting-api/job-board/<slug> (publishedAt)
  - SmartRecruiters: https://api.smartrecruiters.com/v1/companies/<slug>/postings (releasedDate)
  - Workday and other careers sites: WebFetch the posting page itself; it is live only if it shows the job description and an apply option, with no "no longer available", "job not found", "removed" or "closed" notice.
Practical notes: use WebFetch for these, not curl (the shell usually can't reach job sites). Ask WebFetch to list only the titles that match Fish's lanes. Big boards get cut off; when WebFetch says the page continues, call it again with the offset it gives until you've read the whole board. For Greenhouse jobs, store the URL as https://job-boards.greenhouse.io/<slug>/jobs/<id> (the website checks that form directly), even if the board lists a company careers-site link. A site:job-boards.greenhouse.io or site:jobs.lever.co web search for the target titles is a good way to find new companies; then confirm each hit through its API (a 404 there means closed).
Scan at least 20 companies from companies.md each run, rotating through the list so all of them are covered every few days; note in companies.md the date each was last checked. If you can't find a company's board after a short look, mark it "board not found" and move on.

Step 2, discovery (free boards and web search: Mediabistro, Built In LA, The Muse, EntertainmentCareers.net, ProductionHUB, Mandy, StaffMeUp, and searches for the titles above). These are only for finding leads. Every lead found this way must be traced to the employer's own posting and confirmed live there before it goes in. If you can't find the employer's posting, leave it out. If you find a good company not in companies.md, add it with a one-line reason.

URLs that may NEVER be stored in jobs.json: search-results or category pages (anything with /jobs/s/, ?q=, /search), a company's whole job list instead of one posting, URLs with invented #anchors, and third-party aggregators or re-posters (The Ladders, The Muse, Built In, Scoutify, Inference Jobs, iHire, Remotive, Indeed, LinkedIn, ZipRecruiter, ShowbizJobs or any paid board). The one exception: EntertainmentCareers.net or ProductionHUB individual job pages (a single posting with its own ID), when the employer has no posting of its own and the page shows the job open.

DATES
"posted" is the real posting date from the employer page or ATS (first_published, createdAt, publishedAt, releasedDate, or "posted N days ago" converted to a date). If no real date is shown, set "posted" to "" and never fill it with today's date. "found" is the date this scan first saw it. Include postings from the last 30 days, plus older ones that are confirmed open today.

EVERY RUN, BEFORE ADDING ANYTHING: RE-CHECK THE EXISTING LIST
Re-open every job already in jobs.json the same way (ATS API or posting page). Update "verified" to today if still open. Remove it if it is closed, past its "closes" date, not found, or its URL is a forbidden type above. Do not remove a job just for being old: if it is confirmed open today it stays (say "open since <month>" in the note when it was posted more than 60 days ago). Note that a board's job LIST can lag; a job is closed when its own record (.../jobs/<id>) returns 404, even if it still appears in the list. If a page won't load at all (timeout, blocked), keep it one more day and try again next run; remove it after two consecutive failed checks (track with "check_failures": n).

APPLIED
applied.md lists jobs Fish has applied to. Set "status": "applied" on any matching job (match on company + title), keep it on the list while it's open, and never announce it as new. All other jobs get "status": "open".

DUPLICATES
Skip a job if the same URL, or the same company + title + location, is already in the file.

FRIENDS' LIST
Also add up to 10 new "all" listings per day for Fish's friends who are job hunting: writing, creative and production jobs (including below-the-line roles such as coordinators, editors and production managers) at brands, agencies, studios and entertainment companies, LA-area or remote. Same verification and URL rules apply.

UPDATE THE REPO
- jobs.json format: {"updated": "<ISO timestamp>", "jobs": [ ... ]}. Each job is {"id", "company", "title", "type", "location", "pay", "posted" (YYYY-MM-DD or ""), "closes" (YYYY-MM-DD or ""), "url", "lane" (short category), "for" ("fish" or "all"), "status" ("open" or "applied"), "note" (one honest line: why it fits Fish or what the stretch is; for "all" a one-line description), "found" (YYYY-MM-DD), "added" (YYYY-MM-DD), "verified" (YYYY-MM-DD, the last day you confirmed it open), "check_failures" (number, omit when 0)}.
- Notes never start with "Unverified".
- Commit with a short message such as "Daily scan: 2 new for Fish, 5 new for all, 3 removed" and push directly to main (git push origin HEAD:main). The website reads main.
- Never put any secret, token or password in the repo.

REPORT
- Write the digest in this session: new matches for Fish, strongest 3 first, each with company, title, type, location, pay if listed, posted date, the fit note and the link; then how many jobs were removed and why (closed, too old, bad link); then the count of new "all" listings; then which companies were checked; then a Sources list.
- Only if there is at least one new "fish" match, send one PushNotification wrapped in <routine_summary> tags. Lead with the single best match, list the rest a line each, and end with "Full list: andymcelfresh.com/jobs/".
- If nothing new turned up for Fish, still commit the re-check and any "all" updates, and send no notification.
- If the repo isn't present in the working directory, or the push fails, send a PushNotification saying exactly what failed (for example "job-leads repo not attached to the scheduled task" or "push to main rejected") and stop. Don't try workarounds.
