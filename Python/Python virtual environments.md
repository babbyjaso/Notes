- what if we needed a certain version of a script for one thing and a different version of that script for another?
- virtual environments solves this!
- basically its own environment that isn't dependent on the host system
- to make your own virtual environment:
	- `python3 -m venv virtual-env`
		- this creates the directory that the virtual environment will exist in
	- `.virtual-env\Scripts\activate`
		- this starts the virtual environment
		- you'll see a `(virtual-env)` on the cmd at the beginning when it's activated
	- `deactivate`
		- gets you out of the VE