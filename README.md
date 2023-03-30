# The NuHome ERP built on Odoo

Install Odoo into the virtual environment:

```shell
pip install -e ~/Developer/Library/Odoo/odoo
```

Now install Odoo libs:

```bash
pip install -r ~/Developer/Library/Odoo/odoo/requirements.txt
pip install -r requirements.txt
```

# Development

First pull all submodules:

```shell
git submodule update --init --recursive
```
Remember to set up the installed modules in the development branches to prevent Odoo.sh installing and testing all submodules.

To update submodules:

```bash
git pull --recurse-submodules
```

## Adding new Submodules

```bash
git submodule add -b 16.0 git@github.com:contagra/odoo-contagra src/contagra
```

## Removing Submodules

```bash
git submodule deinit <path_to_submodule>
git rm <path_to_submodule>
git commit -m "Removed submodule "
rm -rf .git/modules/<path_to_submodule>
```

## Uninstall module from the command line

Run this command in your shell

```shell
python odoo-bin shell -d mydb --addons-path=/your/addons/path
```
Then run this python script

```shell
self.env['ir.module.module'].search([('name', '=', 'crm')]).button_immediate_uninstall()
```

