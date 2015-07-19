Integrate Trello and HipChat
============================

(Based on <https://github.com/rasky/trello-hipchat>)

Send important Trello activity logs to Slack channels.

This program will monitor multiple Trello boards/lists and send notifications
to multiple Slack channels. You can monitor a whole board, or just a specific
subset of lists within it.

Currently, the following Trello activities are notified for all the specified
lists/boards:

   * Creation of a card
   * Comments being added to a card
   * Attachments being added to a card
   * Moves of cards between lists, if etiher the old or the new list is
     among the monitored ones
   * Completion of checklist items within a card

This subset of actions (with a carefully tuned whitelist of lists) should give
a good balance and report important notifications to the whole development team.


How to install
==============

  * Copy the program to some Linux server you have access to.
  * Copy the sample configuration from `trello-slack.cfg.sample` to
    `trello-slack.cfg`.
  * Go through the configuration, read the comments and follow all the
    instructions to get all the required API keys, tokens, IDs, etc.
  * Run trello-slack.py within cron. You can use `crontab -e` to edit
    the current user's crontab file, and add a line like this to run
    the program every minute and redirect its logs to syslog:

         * * * * * /path/to/trello-hipchat.py 2>&1 | logger
