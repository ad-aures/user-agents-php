# user-agents-php
This is a dummy PHP implementation for [opawg / user-agents](https://github.com/opawg/user-agents)

## Installation

### Via composer

- Add `podlibre/user-agents-php` to your `composer.json`.
- Add `post-install-cmd` / `post-update-cmd` scripts to your `composer.json` so that the class is generated.

```
{
  "require": {
    "podlibre/user-agents-php": "*"
  },
  "scripts": {
    "post-install-cmd": "@php vendor/podlibre/user-agents-php/src/UserAgentsGenerate.php >  vendor/podlibre/user-agents-php/src/UserAgents.php",
    "post-update-cmd": "@php vendor/podlibre/user-agents-php/src/UserAgentsGenerate.php >  vendor/podlibre/user-agents-php/src/UserAgents.php"
  }
}
```

### Manually
- Clone git repository where you need it:

```
$ git clone https://github.com/podlibre/user-agents-php.git
```

- Generate the class:

```
$ php src/UserAgentsGenerate.php >  src/UserAgents.php
```

Or with composer:

```
$ composer run-script post-install-cmd
```

## Usage
When you need it, just call `\Podlibre\UserAgentsPhp\UserAgents::find()`:

```
$player = \Podlibre\UserAgentsPhp\UserAgents::find($_SERVER['HTTP_USER_AGENT']);
if($player){
	print player['app']."\n";
	print player['device']."\n";
	print player['os']."\n";
	print player['bot']."\n";
} else {
	print "This user-agent was not found.\n";
}
```
