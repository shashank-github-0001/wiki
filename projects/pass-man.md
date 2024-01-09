# this is the pass-man password manager

## what should the app do
* Storing passwords: Allow users to securely save passwords for various websites and services.
* Retrieving passwords: Enable users to easily retrieve saved passwords when needed.
* Encryption: Protect all stored passwords using robust encryption methods (e.g., AES-256).
* User authentication: Require a master password to access the password vault.

## additional func
* Password generation: Generate strong, unique passwords for new accounts.
* Password editing: Allow users to modify existing passwords.
* Password organization: Provide features to categorize and group passwords for better management.
* Searching: Enable users to quickly find specific passwords using keywords.
* Command-line integration: Integrate with other command-line tools for seamless password management.
* Secure clipboard: Copy passwords to the clipboard without leaving traces in plain text.
* Timeout: Automatically lock the password vault after a period of inactivity.
* Backup and restore: Offer options to back up and restore password data.
* Password strength assessment: Analyze the strength of saved passwords and suggest improvements.
* Session locking and unlocking: Allow users to temporarily lock the session for added security.
* Custom fields: Provide the ability to store additional information related to passwords, such as usernames, security questions, and notes.

## considerations
* User experience: Design a clear and intuitive interface for easy interaction.
* Security: Prioritize security measures throughout development and testing.
* Platform compatibility: Ensure the manager works across different operating systems.
* Extensibility: Allow for future feature additions and customization.

## how do i make this basic things
* just do a surrealdb based storage
* first ill give them a few options when they run the cli
    * do you want to generate a password
        * after you generate do you want to discard it or store it
        * if yes give the site for which you are storing that password
        * if no then just discard it
    * verify the user and just list the passwords and print them to stdout if 
    * and everytime you store the data then encrypt the files
    * allow them to replace a password if they want to
