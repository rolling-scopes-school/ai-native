# BEVN-115: Registration modal shows stale data after close

> Frontend fix | Both tracks | Free-form
>
> Rules and route: [README.md](../README.md)

The registration modal keeps its state after it closes. Partially entered form data appears when the modal is reopened, and a completed registration leaves the success screen visible on the next open.

Reset the modal whenever it closes so each open starts with a fresh form.

## Definition of done

- [ ] Closing the modal clears all form fields
- [ ] Closing the modal clears validation errors and server error messages
- [ ] Reopening the modal after a successful registration shows a fresh empty form
- [ ] Repeated open and close cycles do not retain or accumulate state
