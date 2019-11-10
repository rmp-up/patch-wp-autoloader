# Contribution

> Remember that each patch you write may change up to millions of websites.

## Specs

We like to see **commit messages** in the format "<topic>: <heading>"
followed by some details.
This way we can generate a changelog more easily.


## Creating a patch

The WordPress installer does not support the `--prefer-source` option
so we need to make a little workaround to generate a patchfile:

```bash
cd html
git init . && git add -A && git commit -m 'tmp'
# Now start changing stuff
git diff
```


After running `composer  install` you'll have a copy of WordPress in the "html/"
directory.

## Testing locally

First of all you are free to use whatever you need for testing locally.
It would be nice if it is documented in the repo as well.
So far we provide a docker boilerplate which can be used like this:

```bash
chown :www-data .
docker-compose up -d
docker-compose exec --user=www-data php bash
composer install
```

The first run may take a while because it will build the docker container.
By now you may already see a website when browsing http://10.221.13.71 .

If something went wrong with the IP-Pool then replace the ".221.13." part
with anything else (e.g. ".13.37." or other).
If you are having trouble deleting
or changing files then either
`docker-compose exec php find * -type d -exec chown :www-data {} \;` helps
or your local user is not in the www-data group.
If you change the Dockerfile then you need to rebuild the container using
`docker-compose build`.
Contact your SysOps for help on these and further topics.

## Register as "patch/..." package

By now the namespace "patch/" can only be used by a set of persons.
You can join this namespace if your patch meets the following specs:

1. Updates and contribution is guaranteed for the next 3 years
2. Version-Tags are the same as the underlying software (e.g. WordPress, Magento)
3. Tests (with CI) and documentation has been added

If you feel good about the most important parts then lets have a talk.
