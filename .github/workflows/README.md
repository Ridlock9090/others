# 1. hello.yml

This code defines a GitHub Actions workflow named "Hello world workflow." It is triggered by three events: when code is pushed to the `main` branch, when a pull request is made to the `main` branch, and when it is manually dispatched.

The workflow consists of two jobs:

1. **hello**: 
   - Runs on the latest version of Ubuntu.
   - Checks out the code using the `actions/checkout` action.
   - Executes a step that prints "Hello world" to the console.

2. **goodbye**: 
   - Also runs on the latest version of Ubuntu.
   - Executes a step that prints "Goodbye world" to the console.

Both jobs use the Bash shell for their commands.

---

# 2. issue_comment.yml

This code defines a GitHub Actions workflow called "Create a comment on new issues." It triggers when a new issue is opened in a repository.

### Key Components:

- **Event Trigger**: The workflow activates on the `opened` type of issues.

- **Permissions**: It specifies that the workflow has permission to write to issues.

### Jobs:

1. **comment-with-action**:
   - Runs on the latest version of Ubuntu.
   - **Steps**:
     - **Dump GitHub Context**: Outputs the GitHub event context in JSON format using `jq` for formatting.
     - **Create Comment**: Utilizes the `peter-evans/create-or-update-comment` action to comment on the newly opened issue. The comment is multi-line and includes Markdown formatting, along with a reaction of "+1."

2. **comment-with-api**:
   - Runs on the latest version of Ubuntu.
   - **Steps**:
     - **Create Comment with API**: Uses a `curl` command to send a POST request to the GitHub API to add a comment to the issue. The comment is specified in the request body. It uses environment variables to dynamically get the organization, repository, and issue number.

Overall, the workflow comments on newly opened issues using both an Action and a direct API call.

---


