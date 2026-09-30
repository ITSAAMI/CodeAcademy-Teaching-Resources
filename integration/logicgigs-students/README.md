# LogicGigs student integration (CERT001–CERT046)

Cleaned data for the 46 B01–B07 Full-Stack alumni. The **LogicGigs local session** (the one on the Windows
machine at `D:\xampp\htdocs\logicgigs`) applies it to the database. Nothing here changes LogicGigs by itself.

## Files
- `students-merged.json`: the uploaded `students.json` merged with the student tables in this repo's `README.md`.
- `avatars/placeholder-male.svg`, `avatars/placeholder-female.svg`: illustrated placeholder avatars. Students replace them later.

## Owner decisions (2026-09-30)
| Topic | Decision |
|---|---|
| Match key | `certificate_id` → the existing CERT001–046 accounts |
| Names | Keep the names already in the DB. `name_in_json` is for reference only |
| Profile images | Skip every JSON image (randomuser.me / missing local file). Use the placeholder avatar for `gender_inferred` |
| Projects | Real. Assign them to each student with `github_url = null`, then ask each student (existing notifications) to send the GitHub link and add **itsaami42@gmail.com** as a collaborator on the repo |
| Attendance | Real. Store `attended/total` (e.g. 68/76) |
| Fields missing from both sources (email, phone, etc.) | Leave NULL. Neither source has them |

## Clean-up already applied
- Removed the UTF-8 BOM. Fixed the garbled `Eâ€‘Commerce` text (CERT036). Dropped the `"Not Submitted"` placeholders (78 real projects remain).
- `status` and `status_note` come from the README: 18 completed, 2 partial, 26 incomplete.
- CERT041 is marked `readmitted_in: FS_B9`.

## Still needs approval before applying (see the chat)
1. Schema: if the DB has no place for attendance, status, gender, or project GitHub links, **do not add columns without the owner's yes**.
2. `gender_needs_confirmation`: CERT003 Sanabil, CERT021 Sabeel, CERT038 Saddan.
3. CERT029, 032, 035, 039, 044, 046: the README says incomplete (low or no attendance), but the JSON gives them projects. Default: assign the projects and keep the incomplete status.
