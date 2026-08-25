# BEVN-101 — Sessions Page Is Slow

> Optional — SQL Performance · both tracks · free-form · Track B: do it BEFORE EXT-150
> Rules & route: [README.md](../README.md)

Users are complaining that opening a conference page takes noticeably longer when the conference has many sessions. No errors, the data loads — it's just slow. Find out why and fix it. The data returned must stay the same.

**Definition of Done:**
- [ ] Root cause identified and documented in a code comment at the fix location
- [ ] Fix applied to all affected service methods
- [ ] The number of SQL queries executed for the sessions endpoint is bounded regardless of session count
- [ ] No existing endpoint returns different data than before
- [ ] PR description explains what was happening and what changed
