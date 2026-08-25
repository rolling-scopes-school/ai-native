# BEVN-115 — Registration Modal Shows Stale Data After Close

> Frontend Fix · both tracks · free-form
> Rules & route: [README.md](../README.md)

When a user opens the registration modal, partially fills in the form, and then closes it, the fields still contain the old data the next time the modal is opened. After a successful registration, reopening the modal shows the success screen instead of a fresh form — making it impossible to start a new registration without refreshing the page.

**Definition of Done:**
- [ ] Closing the modal resets all form fields to empty
- [ ] Closing the modal clears any validation errors and server error messages
- [ ] After a successful registration, reopening the modal presents a fresh empty form
- [ ] Multiple open/close cycles do not accumulate state
