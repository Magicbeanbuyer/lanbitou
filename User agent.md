User agent is part of the HTTP request?
User-agent is a string including information like:

- device type (is it a mobile or a laptop?)
- device version (the operating system version and browser name)
- software application name
User agent would also have information on if the user is a bot, like Google's crawler. Google bot would be part of the user agent string.
Google bot crawls the public internet to form an index database for its [[search engine]].
Each website has a robot.txt file in its root directory to specify what bots are allowed to crawl its website or not allowed.

[[ChatGPT]] uses three different kinds of user-agents:
OAI-Search Bot: This bot is used to search the internet on behalf of users 
GPTBot: this is the bot used to scrape web contents to train their model 

| Role                 | Anthropic                    | OpenAI          |
| -------------------- | ---------------------------- | --------------- |
| Training crawler     | `ClaudeBot` / `anthropic-ai` | `GPTBot`        |
| Search indexer       | `Claude-SearchBot`           | `OAI-SearchBot` |
| User-triggered fetch | `Claude-User`                | `ChatGPT-User`  |

## Links
- [Overview of OpenAI Crawlers](https://developers.openai.com/api/docs/bots/
- [Does Anthropic crawl data from the web, and how can site owners block the crawler? | Claude Help Center](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler)
- 

