# Experience Users

An Experience User is a unique user registered to your application's Experience. Users can access protected [endpoints](/experiences/endpoints/), and you can build profiles against each user.

## Viewing Experience Users

![Experience Users](/images/experiences/users-list.png "Experience Users")

Users are listed within the "Users" tab of your application's "Experience" subsection. Click the user's email address in the list to view and to edit his / her profile.

## Adding an Experience User

![Add User](/images/experiences/add-user.png "Add User")

From the Users list page, click "Add User" in the top right corner. This will take you to a page where the new user can be configured.

## User Configuration

There are a number of fields that can be set for a user, some of which are required.

### Required Fields

![Required User Fields](/images/experiences/user-required-fields.png "Required User Fields")

*   **Email Address**: This must be a valid email address, and it must unique across your application. It is possible to register Experience Users with the same email address across multiple applications, but each user will count against your [resource limits](/organizations/resource-limits/).
*   **Password**: A user's password must be at least 8 characters long. When creating a user, this field must be set; when updating a user, it is not necessary to assign the user a new password unless you have checked the "Change password?" box.

The combination of these two values is what your Experience Users will use to [authenticate](/workflows/experience/authenticate/) against your application.

### Optional Fields

![Optional User Fields](/images/experiences/user-optional-fields.png "Optional User Fields")

*   **First Name** and **Last Name**: The user's first and last names. These can be any string, or they can be left blank. You may also set one but not the other.
*   **Group IDs**: Any [Experience Groups](/experiences/groups/) the user should be a member of. Note that it is possible to create new groups directly from this interface, with the edited user automatically being added to the group. Simply type the name of a group that does not yet exist.

### User Tags

![User Tags](/images/experiences/user-tags.png "User Tags")

Tags allow for the storing of arbitrary data against any Experience User. Tags are useful for:

*   Storing additional profile information, such as phone number or street address
*   Categorizing users into groups
*   Mapping Experience Users to other services, such as Facebook or Twitter, by storing their third-party IDs

A tag's key may only include uppercase and lowercase letters; numbers; and hyphens (-) and underscores (\_). A tag's value can be any arbitrary string. A key may only be set once per user; you may not, for example, store the variable `facebookId` as two separate values for one user.

Any tag keys that have been used with other Experience Users will be available as "autosuggest" options when you enter new keys.

## Invalidating User Tokens

From a user's edit page, you have the option of invalidating any authorization tokens assigned to that user. This is useful if, for example, you believe the user's account was compromised.

![Invalidate User Tokens](/images/experiences/user-invalidate-tokens.png "Invalidate User Tokens")

Invalidating a user's tokens simply means that the user must re-authenticate using their email and password before they can make any more requests to [authenticated endpoints](/experiences/endpoints/#access-control). It does not take any destructive action on the user, nor does it automatically change their password.

## Deleting Users

A user can be deleted by clicking the "Delete" icon next to any user on the list page, or by clicking the "Delete" button in the footer of a user's edit page. Deleting a user will automatically remove him / her from any of their [Experience Groups](/experiences/groups/).
