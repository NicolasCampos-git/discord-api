# Foobara::DiscordApi

This gem provides an easy way to use the Discord API via Foobara commands.

## Installation

Add `gem foobara-discord-api` to your Gemfile or .gemspec file. Or even just
`gem install foobara-discord-api` if just playing with it directly in the scripts. 

## Usage

### Discord setup and credentials

To use the `foobara-discord-api` gem, you'll need a Discord bot/Discord API token and the ID of a channel where the bot can send messages. 

### Send a message

Require the gem and run the command with the destination channel ID and the message content:

```ruby
require "foobara/discord_api"

command = Foobara::DiscordApi::CreateMessage.new(
  channel_id: ENV["DISCORD_CHANNEL_ID"],
  content: "Hello, Discord!"
)

outcome = command.run

if outcome.success?
  message = outcome.result
  puts "Created message #{message.id} in channel #{message.channel_id}"
else
  puts outcome.errors_hash
end
```

If `api_token` is omitted, the command falls back to the `DISCORD_API_TOKEN` environment variable. To pass it explicitly:

```ruby
command = Foobara::DiscordApi::CreateMessage.new(
  channel_id: ENV["DISCORD_CHANNEL_ID"],
  content: "Hello, Discord!",
  api_token: "your-bot-token"
)

outcome = command.run

if outcome.success?
  message = outcome.result
  puts "Created message #{message.id} in channel #{message.channel_id}"
else
  puts outcome.errors_hash
end
```

## Contributing

Bug reports and pull requests are welcome on Github at https://github.com/foobara/discord-api

Before you get started, ensure you have Ruby installed (via RVM or a similar version manager).

To work on an existing issue or submit a PR:
1. Fork the `foobara/discord-api` repository and clone it to your local machine.
2. Run `bundle install` to install any dependencies.
3. Run `rake` to ensure that everything works as expected before making any changes.
4. Implement your changes adding tests where applicable.
5. Re-run `rake` to ensure that all tests and RuboCop still pass.
6. Commit, push to GitHub and open a PR to review.

## License

This project is licensed under the MPL-2.0 license. Please see [LICENSE.txt](LICENSE.txt) for more info.