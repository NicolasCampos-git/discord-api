# Foobara::DiscordApi

This Ruby gem provides an easy way to use the Discord API via Foobara commands.

## Installation

Typical stuff: add `gem foobara-discord-api` to your Gemfile or .gemspec file. Or even just
`gem install foobara-discord-api` if just playing with it directly.

## Usage

### Discord setup and credentials

To run `CreateMessage`, you'll need a Discord bot/Discord API token and a channel ID.

### Send a message

Require the gem and run the command with the destination channel ID and the message content:

```ruby
require "foobara/discord_api"

outcome = Foobara::DiscordApi::CreateMessage.run(
  channel_id: "some-channel-id",
  api_token: "some-api-token",
  content: "Hello, Discord!"
)

if outcome.success?
  message = outcome.result
  puts "Created message #{message.id} in channel #{message.channel_id}"
else
  puts outcome.errors_hash
end
```

The `api_token` input can be omitted and defaults to `ENV["DISCORD_API_TOKEN"]`.

## Contributing

Bug reports and pull requests are welcome on Github at https://github.com/foobara/discord-api

To work on an existing issue or submit a PR:

1. Fork the `foobara/discord-api` repository and clone it to your local machine.
2. Run `bundle install` to install any dependencies.
3. Run `rake` to ensure that everything works as expected before making any changes.
4. Implement your changes.
5. Re-run `rake` to ensure that all tests and RuboCop still pass.
6. Commit, push to GitHub and open a PR for review.

## Help

If you need help using or contributing to this gem,
find us on Discord at [https://discord.gg/dDpdFAeCHB](https://discord.gg/dDpdFAeCHB)
and ask away!

## License

This project is licensed under the MPL-2.0 license. Please see [LICENSE.txt](LICENSE.txt) for more info.
