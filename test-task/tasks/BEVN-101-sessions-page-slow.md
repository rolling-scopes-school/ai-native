# BEVN-101: Sessions page is slow

> Optional | SQL performance | Both tracks | Free-form
>
> Track B: complete this task before EXT-150
>
> Rules and route: [README.md](../README.md)

Opening a conference becomes slower as the number of sessions grows. The data still loads and no error is reported. Find the cause and fix it without changing the returned data.

## Definition of done

- [ ] Identify the root cause and document it in a code comment at the fix location
- [ ] Apply the fix to every affected service method
- [ ] Keep the number of SQL queries for the sessions endpoint bounded as the session count grows
- [ ] Preserve the data returned by all existing endpoints
- [ ] Explain the cause and the fix in the Pull Request description
