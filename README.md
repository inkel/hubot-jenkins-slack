# [Hubot][hubot] Jenkins notifier for [Slack][slack]
Respond to [Jenkins][jenkins] notifications in a format appropiated for [Slack][slack] [attachments][slack-attach].

## Installation
In hubot project repository, run:

```
npm install hubot-jenkins-slack --save
```

Then add `hubot-jenkins-slack` to your `external-scripts.json`:

```json
[
  "hubot-jenkins-slack"
]
```

You also need [slack-attachment](https://github.com/inkel/hubot-slack-attachment) module installed for version 3 of hubot-slack adapter.

## Screenshots
Below you could see a sample session of `hubot-jenkins-slack` with:

1. a build that finalized with success;
2. a build that starts from our `master` branch;
3. a build that failed;
4. a build that starts from a pull request.

![attachments][attachments]

The obscured information in the first line of each notification follows the following pattern: `Jenkins #{job name} #{action} #{job build URL}`.

## Configuration

### Jenkins
You need to enable Jenkins [Notification plugin][notification-plugin] and then, in each project you would like to be notified about, add an endpoint like the following:

![Add Notification endpoint][notification-endpoint]

You only need to change `URL` to point to your host. Take into account that the URL path begins with your Hubot instance name, so if your Hubot is named `marvin`, the URL should be `http://example.com/marvin/jenkins` instead.

The `room` query string parameter is required, as an indicator of the channel name where you would like your notification to be displayed. You don't need to prefix your room name with `#`, so if you want your notifications displayed in the `#ci` channel, then you need to pass `?room=ci`.

In case you want to see the message received and the attachment sent, you can also pass `debug=1`.

### Environment variables
The following environment variables define the colors used for each build status:

* `HUBOT_JENKINS_COLOR_ABORTED`
* `HUBOT_JENKINS_COLOR_FAILURE`
* `HUBOT_JENKINS_COLOR_FIXED`
* `HUBOT_JENKINS_COLOR_STILL_FAILING`
* `HUBOT_JENKINS_COLOR_SUCCESS`
* `HUBOT_JENKINS_COLOR_DEFAULT`

## Commands
This plugin currently offers no commands.

## License
This software is licensed under MIT License. See [License][license] for more details.

[hubot]: https://hubot.github.com/
[jenkins]: http://jenkins-ci.org/
[slack]: https://slack.com/
[slack-attach]: https://api.slack.com/docs/attachments
[license]: https://github.com/inkel/hubot-jenkins-slack/blob/master/LICENSE
[notification-plugin]: https://wiki.jenkins-ci.org/display/JENKINS/Notification+Plugin
[notification-endpoint]: screenshots/notification-endpoint.png
[attachments]: screenshots/attachments.png
