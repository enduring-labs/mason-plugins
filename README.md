# Mason

Mason helps property managers investigate maintenance work orders, prepare
resident and vendor communications, and understand their maintenance backlog.
This plugin pairs workflow skills with the remote Mason MCP connector. It
requires an existing authorized Mason account and access to the property manager
you select during OAuth consent.

## What you can ask

- **Investigate an issue:** “Why is the kitchen sink repair at 123 Example Street
  still open? Show the evidence and the next decision.”
- **Prepare a communication:** “Draft an update to the resident about that
  appointment. Don't send it.” When you ask to send or schedule a message, Mason
  checks the current workflow, recipient context, and permissions.
- **Review the portfolio:** “Summarize my open maintenance work orders and the
  items that need attention.” Reports disclose their scope and missing data.

The skills are `mason-maintenance-triage`, `mason-communications`, and
`mason-maintenance-digest`. They guide tool selection and reporting; live Mason
account policies remain available through the connector. The skills do not grant
access or independently authorize actions.

## Connect your account

Install the plugin in a supported host, then connect Mason using its OAuth flow.
In Claude, open the plugin's Connectors tab and connect Mason. In ChatGPT, follow
the plugin's connection prompt. Confirm the selected property manager and scopes.
The remote endpoint is <https://mason.enduring-labs.com/api/mcp>.

- `mason.read` retrieves records and workflow references within your connection.
- `mason.write`, when additionally consented, permits the changes and workflows
  available to your account. Successful writes execute immediately under your
  host's tool permissions. Some workflows notify people, send messages, or call.

Ask “Which Mason user and property manager am I connected as?” to check the
connection. A read-only connection cannot write even when a prompt approves an
action. To change scopes, reconnect and give fresh OAuth consent. Revoke access
in Mason → Settings → Connected apps. Revocation does not delete business records
or existing audit history.

## Behavior and data handling

The plugin contains text skills, manifests, and a logo. It installs no executable,
local MCP process, hook, background job, or permission override. Its MCP server
configuration connects only to Mason's fixed HTTPS endpoint. It does not request
local files, environment credentials, or the host's entire conversation history.

Requested tool calls send their arguments to Mason and return account-scoped
business data, which may include contact information and communications. Mason
may consult the property manager's configured integrations to fulfill an action.
Authorized workflow and communication tools may notify people through those
integrations. A draft remains a draft unless you request further action. A queued
message is not proof of delivery. Stop Mason and the server's other safeguards
remain enforced; a blocked communication is not permission to switch channels.

The host processes information under its own terms and plan; installing this
plugin does not place a personal AI account under Mason's provider agreements.
See the [connector privacy notice](https://mason.enduring-labs.com/docs/mcp/privacy)
and [terms](https://www.thisismason.com/legal/terms).

## License

This plugin is proprietary and distributed under the [Mason Plugin Limited Use
License](LICENSE). You may install and use it with an authorized Mason account,
including for business use and internal deployment to authorized users.
The license restricts redistribution, modification, and reuse of its skill
instructions in other products, including competing services. It permits
authorized platform distribution and preserves rights granted under applicable
platform terms and law. Public source visibility does not grant general reuse
rights. The included name and logo identify Mason; they do not authorize
rebranding or endorsement. See LICENSE for the complete terms.

## Support

See the [connection guide](https://mason.enduring-labs.com/docs/mcp) or contact
[hello@thisismason.com](mailto:hello@thisismason.com). For an unexpected result,
include the work-order link and approximate time, without passwords or tokens.
If an action's result is uncertain, inspect Mason before repeating it.
