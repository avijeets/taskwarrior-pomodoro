# Taskwarrior-Pomodoro

![](http://coddingtonbear-public.s3.amazonaws.com/github/taskwarrior-pomodoro/screenshot.png)

A simple application allowing you to use Pomodoro techniques with Taskwarrior on OSX.

## Why 52?

> "25 minutes of work is just not enough. By the time you are really in the thick of something, you have to stop? Plus, nothing can really be accomplished or replenished by 5 minutes of rest. That’s just enough to get to the bathroom and back. It made more sense to me to assimilate tasks into a longer work time than to think of tasks in increments of work time."

Read more about the 52:17 method experiment [here](https://medium.com/@tristadedmon/my-52-17-method-experiment-8d2769fb946d#.8hf6jtidw).

Simply put, the Pomodoro Technique has the right idea but isn't the sweet spot for producivity. 52 minutes of producivity and 17 minutes of rest leave with enough time within each pool to actually finish a fruitful amount of work while still having a downtime to still do something fun.


## Installation

You can [download the latest release here](http://coddingtonbear-public.s3.amazonaws.com/github/taskwarrior-pomodoro/releases/taskwarrior-pomodoro-1.5.0.dmg), and install it by dragging the application into your Applications directory.

## Configuration 

Configuring Taskwarrior Pomodoro is handled by adding lines to your `~/.taskrc` file.  See below for what features you can configure.

### Taskwarrior Application Path

Taskwarrior-pomodoro relies on your local installation of Taskwarrior for interacting with your task list.  It will search in several common places for the `task` app, but if you would like to override the path it selects by default or have installed `task` into an uncommon location, you can override it by setting the key `pomodoro.taskwarrior_path` in your `~/.taskrc`.

```
pomodoro.taskwarrior_path=/path/to/task
```

### Task List Filter

By default, the list of tasks is limited to displaying only tasks that are currently pending (`status:pending`), but you can specify any filter you'd like for further reducing that list by setting the key `pomodoro.defaultFilter` in your `~/.taskrc`.

While at work, for example, you could limit your tasks to only pending tasks having the `work` tag by adding a line as follows:

```
pomodoro.defaultFilter=+work
```

Note that taskwarrior filters can be quite complex (although my specific use of this feature will not be particularly helpful, it may help you come to terms with what is possible by knowing that the one I used for generating the above screenshot was `pomodoro.defaultFilter=(intheamtrellolistid:5591ecedb12a520b50d2e8b8 or intheamtrellolistid:559173de3295c9b2e550243f or intheamtrellolistid:55aee69377ccc07e295462a3) and (-work)`) and are thus outside the scope of this document, but you can [find more information about filters in Taskwarrior's documentation](http://taskwarrior.org/docs/filter.html).

### Task List Sorting

To enable sorting you need to set `pomodoro.default.sort` key.

```
pomodoro.default.sort=project+,urgency-
```

To find more, take a look into sorting section in [Taskwarrior's reports documentation](http://taskwarrior.org/docs/report.html).

### Post-Pomodoro Hook

* [Taskwarrior-Pomodoro-Beeminder](https://github.com/coddingtonbear/taskwarrior-pomodoro-beeminder) provides functionality allowing you to increment Beeminder goals using this "Post-Pomodoro Hook" functionality.

You can configure Taskwarrior Pomodoro to call a script of your choice after you complete a Pomodoro.  The script will receive one additional command-line argument: the UUID of the task that you were working on.  You could use this for a variety of things, including updating goal-tracking software or recording billable hours.

```
pomodoro.postCompletionCommand=/path/to/my/script
```

### Pomodoro Counter

By default, Taskwarrior Pomodoro will display a running count of Pomodoros completed during each day.  If you'd like to disable the display of this running count, you can turn it off by setting the ``pomodoro.displayCount`` setting to ``false``:

```
pomodoro.displayCount=false
```

### Pomodoro Duration

By default, Taskwarrior Pomodoro uses standard 25-minute (1,500 second) pomodoros.  You can override the default duration by adding a setting named ``pomodoro.durationSeconds`` setting the number of seconds you'd like a pomodoro to last.  For example; to set your pomodoros to last 45 minutes (2,700 seconds), you could set this setting as follows:

```
pomodoro.durationSeconds=2700
```
