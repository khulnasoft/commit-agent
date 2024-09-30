# CommitMate
<h4>
   A friendly assistant for your commits.
</h4>
<p>
   <a href="https://www.npmjs.com/package/commitmate"><img src="https://img.shields.io/npm/v/commitmate" alt="Current version"></a>
</p>

<p>
   Inspired by the <a href="https://githubnext.com/projects/copilot-cli">GitHub Copilot X CLI</a>, but open source for everyone.
</p>

<br>

# CommitMate

## Setup

> The minimum supported version of Node.js is v14

1. Install _commit mate_:

   ```sh
   npm install -g commitmate
   ```

2. Retrieve your API key from [OpenAI](https://platform.openai.com/account/api-keys)

   > Note: If you haven't already, you'll have to create an account and set up billing.

3. Set the key so commitmate can use it:

   ```sh
   getcommit config set OPENAI_KEY=<your token>
   ```

   This will create a `.commitmate` file in your home directory.

## Usage

```bash
getcommit <prompt>
```

For example:

```bash
getcommit list all log files
```

Then you will get an output like this, where you can choose to run the suggested command, revise the command via a prompt, or cancel:

```bash
◇  Your script:
│
│  find . -name "*.log"
│
◇  Explanation:
│
│  1. Searches for all files with the extension ".log" in the current directory and any subdirectories.
│
◆  Run this script?
│  ● ✅ Yes (Lets go!)
│  ○ 📝 Revise
│  ○ ❌ Cancel
└
```

### Special characters

Note that some shells handle certain characters like the `?` or `*` or things that look like file paths specially. If you are getting strange behaviors, you can wrap the prompt in quotes to avoid issues, like below:

```bash
getcommit 'what is my ip address'
```


```bash
getcommit chat
```

With this mode, you can engage in a conversation with the AI and receive helpful responses in a natural, conversational manner directly through the CLI:

```sh
┌  Starting new conversation
│
◇  You:
│  how do I serve a redirect in express
│
◇  CommitMate:

In Express, you can use the `redirect()` method to serve a redirect. The `redirect()` method takes one argument, which is the URL that you want to redirect to.

Here's an example:

\`\`\`js
app.get('/oldurl', (req, res) => {
  res.redirect('/newurl');
});
\`\`\`
```

### Silent mode (skip explanations)

You can disable and skip the explanation section by using the flag `-s` or `--silent`

```bash
getcommit -s list all log files
```

or save the option as a preference using this command:

```bash
getcommit config set SILENT_MODE=true
```

### Custom API endpoint

You can custom OpenAI API endpoint to set OPENAI_API_ENDPOINT（default: `https://api.openai.com/v1`）

```sh
getcommit config set OPENAI_API_ENDPOINT=<your proxy endpoint>
```

### Set Language


The CommitMate's default language is English, but you can easily switch to your preferred language by using the corresponding language keys, as shown below:

| Language   | Key |
| ---------- | --- |
| English    | en  |
| Spanish    | es  |
| Japanese   | jp  |
| Korean     | ko  |
| French     | fr  |
| German     | de  |
| Russian    | ru  |
| Ukrainian  | uk  |
| Vietnamese | vi  |
| Arabic     | ar  |
| Portuguese | pt  |
| Turkish    | tr  |

For instance, if you want to switch to Simplified Chinese, you can do so by setting the LANGUAGE value to en:

```sh
getcommit config set LANGUAGE=en
```

This will set your language to Simplified Chinese.

### Config UI

To use a more visual interface to view and set config options you can type:

```bash
getcommit config
```

To get an interactive UI like below:

```bash
◆  Set config:
│  ○ OpenAI Key
│  ○ OpenAI API Endpoint
│  ○ Silent Mode
│  ● Model (gpt-3.5-turbo)
│  ○ Language
│  ○ Cancel
└
```

### Upgrading

Check the installed version with:

```bash
getcommit --version
```

If it's not the [latest version](https://github.com/KhulnaSoft/commitmate/tags), run:

```bash
npm update -g commitmate
```

Or just use getcommit:

```bash
getcommit update
```

## Common Issues

### 429 error

Some users are reporting a 429 from OpenAI. This is due to incorrect billing setup or excessive quota usage. Please follow [this guide](https://help.openai.com/en/articles/6891831-error-code-429-you-exceeded-your-current-quota-please-check-your-plan-and-billing-details) to fix it.

You can activate billing at [this link](https://platform.openai.com/account/billing/overview). Make sure to add a payment method if not under an active grant from OpenAI.

## Motivation

I am not a bash wizard, and am dying for access to the copilot CLI, and got impatient.

## Contributing

If you want to help fix a bug or implement a feature in [Issues](https://github.com/KhulnaSoft/commitmate/issues) (tip: look out for the `help wanted` label), checkout the [Contribution Guide](CONTRIBUTING.md) to learn how to setup the project.
