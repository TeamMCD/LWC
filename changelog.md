### 4.00-alpha4
* Flags now support data. No utility to set data yet, however.
* The command `/lwc admin purgeregion <RegionName> [WorldName]` has been added to the WorldGuard module. If you are using it from the console, you must also specify the world that the region is in. If the region is in a different world than the player you use the command from, you must again also provide the world name.
* New updater + downloader. Currently, the default method of updating is via BLEEDING_EDGE. This is a build-by-build update and is currently set to manual by default. You can check your version with `/lwc admin version` and/or update to the latest with `/lwc admin update`. If you want automatic updating, in core.yml set core.updateMethod to: `updateMethod: AUTOMATIC`

### 4.00-alpha3
* **FIX:** Protected blocks could be pulled with a sticky piston
* **FIX:** Piston exploit that allowed protections such as Doors to be destroyed via:  PISTON -> BLOCK -> PROTECTED DOOR
* Towny integration. Protections cannot be made outside of Towns, e.g the wild. Set `core.townyBorders` to true
* Double wooden doors will now function properly
* The openAndClose feature of double doors has been fixed
* Out of sync double doors can be fixed with the `/lwc fix` or `/lwc fixdoor` commands
* Fixes a duplication exploit related to the Magnet feature and the Showcase plugin
* The database is no longer used for LWC's in-memory database. It is now stored in-memory objects and even if the database connection is lost, LWC won't be totally unusable.
* Added the Expire job. It allows you to automatically expire protections - equivilent to `/lwc admin expire`. If you want to expire protections every week, that haven't been accessed in at least 2 weeks, do this: `/lwc schedule create test expire` `/lwc schedule arguments test 2 weeks` `/lwc schedule autoRun test 1 week`  Done! If you want the block + inventory contents of the block to also be removed, you can add -remove after arguments, e.g: `/lwc schedule arguments test -remove 2 weeks`
* Added the Cleanup job. Allows you to automatically run `/lwc admin cleanup`
* Job scheduler. It allows you to manually run specific jobs or automatically run them at a given time (they can be provided by outside sources, too.)
* `/lwc schedule create JOBNAME TYPE` - Creates a job, for example: `/lwc schedule create weekly cleanup`
* `/lwc schedule run JOBNAME` - Manually run a job, for example: `/lwc schedule run weekly`
* `/lwc schedule check JOBNAME` - Look up when the job will next run, if it's to be automatically ran. It will tell you how long until the job runs.
* `/lwc schedule autorun JOBNAME TIME` - Schedule a job to automatically run. For example, run the weekly job every week: `/lwc schedule autorun weekly 1 week` - you can combine times, e.g: `/lwc schedule autorun weekly 2 days 12 hours` = every 60 hours
* `/lwc schedule list` - List all of the known jobs. YELLOW represents a job that is not automatically scheduled and must be automatically ran. GREEN represents a job that is automatically scheduled but is not a candidate to be ran yet. RED represents a job that is waiting to be ran.
* `/lwc schedule arguments JOBNAME ARGUMENTS` - for example: `/lwc create JOBNAME expire` , `/lwc schedule arguments JOBNAME -remove 2 weeks` makes the job JOBNAME which removes protections + blocks of protections that have not be accessed in at least 2 weeks.
* `/lwc tasks` can be used instead of `/lwc schedule`

### 4.00-alpha2
* `/lwc admin report` has had a makeover and now also shows cache read/writes
* Protection rights have been inlined with the main protections table
* Multi-group support has been added for Permissions 3.0+
* Permissions support has been modified to always depend on Superperms, while LWC's own implementations will only be used for groups. This **breaks Permissions 2/3 support** unless you have SuperpermsBridge!