With [!INCLUDE [prod_short](prod_short.md)] 2023 release wave 2, the error handling framework has been enhanced to include promoted actions in both error dialogs and validation errors. These promoted actions are designed to assist users in resolving errors more effectively. There are currently two main scenarios to keep in mind when deciding how to use recommended actions: 
* [Fix-it](../devenv-error-handling-guidelines.md#error-messages-with-fix-it-actions--when-to-use-them) actions are recommended for scenarios where the system knows the correct value that should be used to resolve the error. 
* [Show-it](../devenv-error-handling-guidelines.md#error-messages-with-show-it-actions--when-to-use-them) actions are recommended for scenarios when the system can identify the location where the error may be fixed by the user.

Here are some quick guidelines on when to use each type of error message and its accompanying recommended actions. However, it's essential to begin by considering whether the error could have been avoided in the first place.

| Error type | Description |
|------------|-------------|
|Task dialogs |	Task dialogs are used when an error can be mitigated by the user choosing between two (sometimes three) different options to continue their task without encountering an error.|
|[Error messages with Fix-it actions](../devenv-actionable-errors.md#fix-it-actions) | Fix-it actions can be used when the cause and solution to the error is known and can be solved by users with just one step.|
|[Error messages with Show-it actions](../devenv-actionable-errors.md#show-it-actions) | Show-it actions can be used when an error must be corrected on a related table. A Show-it action can then offer a shortcut to the related table, enabling users to correct the error by themselves with one or multiple steps, while keeping the context of their current task.|