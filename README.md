# Mark24 个人博客


记录生活中的技术和思考


> I think, therefore I am. —— René Descartes


## Tech guide

### config

Run `bundle install` install depencies.
### rake helper

Run `rake --tasks` will list all helpers.

### write blog

When run `rake serve`,you can write blog without care about server build.

### deploy

Run `rake deploy` to deploy the blog to Github Pages.


## Commands

* `rake serve`  or `rake s`  start server

* `rake clean` or `rake c` clean build directory

* `rake build` or `rake b` run clean && build blog static

* `rake deploy` or `rake d` run build && push to Github Pages Repository for generating Github Pages

* `rake push` or `rake p` run `git add * && git commit -m 'update blog' && git push` 

* `rake pd` ==   `rake push && rake deploy`

* `rake new`  create new post

> e.g  rake "new[post-tile]"
