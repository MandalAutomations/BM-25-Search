# Editing an assignment

You can edit existing assignments in your course.

## About editing assignments

After creating an assignment, you can edit many aspects of the assignment to better fit the needs of yourself and your students. Be aware that you cannot change the assignment type (either individual or group) or the online integrated development environment (IDE) after assignment creation. For more information, see [Create an individual assignment](/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-an-individual-assignment) and [Create a group assignment](/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-a-group-assignment).

## Editing an existing assignment

1. Sign into [GitHub Classroom](https://classroom.github.com/login).

2. In the list of classrooms, click the classroom you want to view.

3. In the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-repo" aria-label="repo" role="img"><path d="M2 2.5A2.5 2.5 0 0 1 4.5 0h8.75a.75.75 0 0 1 .75.75v12.5a.75.75 0 0 1-.75.75h-2.5a.75.75 0 0 1 0-1.5h1.75v-2h-8a1 1 0 0 0-.714 1.7.75.75 0 1 1-1.072 1.05A2.495 2.495 0 0 1 2 11.5Zm10.5-1h-8a1 1 0 0 0-1 1v6.708A2.486 2.486 0 0 1 4.5 9h8ZM5 12.25a.25.25 0 0 1 .25-.25h3.5a.25.25 0 0 1 .25.25v3.25a.25.25 0 0 1-.4.2l-1.45-1.087a.249.249 0 0 0-.3 0L5.4 15.7a.25.25 0 0 1-.4-.2Z"></path></svg> Assignments** tab, next to the assignment you would like to edit, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="The pencil icon" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>.

   > \[!NOTE]
   > You can also edit an assignment from the assignment's page. To access the assignment's page, in the **Assignments** tab, click the assignment name.

4. Under "Assignment title," click in the text field, then delete the existing text and type the new assignment title.

5. Optionally, to edit the default prefix for each student's assignment repository, next to the name of the prefix, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="The pencil icon" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>.

   > \[!NOTE]
   > Editing an assignment's title or default repository prefix will not change the name of existing assignment repositories.

   Then, type the new prefix under "Custom repository prefix."

6. Under "Deadline (optional)," click in the text field, then use the date picker to reassign a deadline. The new deadline cannot be in the past, and reassigning a deadline will update the deadline for all students.

   Optionally, to make the deadline a cutoff date, select **This is a cutoff date**. If you use a cutoff date, students will lose write access to their assignment repositories after the cutoff date has passed unless they receive an extension. For more information on extending assignment deadlines, see [Extending an assignment's deadline for an individual or group](/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/extending-an-assignments-deadline-for-an-individual-or-group).

7. To change the status of an assignment, select the **Assignment status** dropdown menu, then click **Active** or **Inactive**.

   > \[!NOTE]
   > Inactive assignments cannot be accepted by students. You should change an assignment status to inactive once no more students should accept an assignment or the assignment deadline has passed.

8. Under "Repository visibility," select a visibility. If you use private repositories, only the student or team can see the feedback you provide.

   > \[!NOTE]
   > Changing the visibility for assignment repositories will not retroactively change the visibility of existing assignment repositories.

9. Optionally, select or deselect **Grant students admin access to their repository**. For more information on admin permissions for repositories, see [About repositories](/en/repositories/creating-and-managing-repositories/about-repositories#about-repository-visibility) and [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

   > \[!NOTE]
   > Granting or revoking student admin access after an assignment has been created will not retroactively change the permissions for existing assignment repositories.

10. To set up or change the template repository for your assignment, in the "Add a template repository to give students starter code" section, select the **Select a repository** dropdown menu.
    * To choose a template repository, begin typing the repository name in the text field, then click the repository in the search results.
    * To remove a template repository, delete any text in the text field.

You cannot change the template repository after a student has accepted the assignment. If you wish to provide updates to the starter code after students have accepted the assignment, see [Making changes to assignment starter code](#making-changes-to-assignment-starter-code).

> \[!NOTE]
> By default, an assignment will create an empty repository for each student on the roster for the classroom.

1. To add a new autograding test, in the "Add autograding tests" section, select the **Add test** dropdown menu, then click a grading method from the options that appear. For more information, see [Use autograding](/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/use-autograding).

   Additionally, you can edit or delete existing autograding tests with <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="The pencil icon" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> or <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="The trash icon" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg>.

2. To add new protected path, in the "Protected file paths" section, type out the file or path and click **Add path**.

   Additionally, delete existing protected paths by clicking <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="The trash icon" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg>.

   > \[!NOTE]
   > If you remove a protected file path, the "Protected file(s) modified" label will be removed from any submissions that edited files in that path

3. To turn feedback pull requests on or off, select or deselect **Enable feedback pull requests**.

   > \[!NOTE]
   > Enabling or disabling feedback pull requests for an assignment will not create or delete feedback pull requests for existing assignment repositories.

4. Click **Update assignment**.

## Making changes to assignment starter code

If you need to update the starter code for your assignment after students have already accepted it, you can do so by modifying the original repository. Since student assignments are based on forks of this repository, you can make changes to the starter code and then create pull requests for students to merge these updates into their assignments. See, [Create an assignment from a template repository](/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-an-assignment-from-a-template-repository).

1. Sign into [GitHub Classroom](https://classroom.github.com/login).

2. In the list of classrooms, click the classroom you want to view.

3. Select the assignment that has a starter code repository.

4. Below the title of the assignment, click the link to your starter code repository.

5. Make the necessary changes to your starter code's content.

6. Return to the assignment overview page.

7. Click **Sync assignments**. If changes are detected, an **Assignments are out of date** button will be shown.

8. To open pull requests in all of your students' assignment repositories, click **Assignments are out of date**.

The pull requests will be titled "GitHub Classroom: Sync Assignment". Ask your students to merge these pull requests.

## Further reading

* [Create an individual assignment](/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-an-individual-assignment)
* [Create a group assignment](/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-a-group-assignment)