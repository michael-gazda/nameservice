# Nameservice Quick Start Guide

## Quick start to using the nameservice module

To start using the nameservice module in your
application there are several necessary steps.

 - Import and initialize AppModules for each used module
 - Register codecs from all modules used
 - AddRoute for handlers and queries
 - InitChainer for initial application state

### Step One

 - Create a new app.go file for your application
 - Define the app name. Example: `const appName = "nameservice"`
 - Import the nameservice module and other needed modules in the import block.

### Step Two
 - Extending BaseApp
     + Create a struct representing your application. Example: `type nameServiceApp struct`
	     * Add all the stores that will be used in your modules
		 * Add the keepers of the modules used
		 * Add the module manager

### Step Three
 - Create a  constructor for your Application (func new<app_name>)
		- Initialize a reference of your application struct
		- Generate storeKeys required by each Keeper.
		- Register Handlers from each module. The AddRoute() method from baseapp's router is used to this end.
		- Register Queriers from each module. The AddRoute() method from baseapp's queryRouter is used to this end.
		- Mount KVStores to the provided keys in the baseApp multistore.

### Step Four
 - Set the initChainer for defining the initial application state. The initChainer defines how accounts in genesis.json are mapped into the application state on initial chain start.

### Step Five
 - Instantiate required Keepers from each desired module.

### Step Seven
 - SetOrderBeginBlockers - Logic that runs before any Tx
 - SetOrderEndBlockers - Logic to run after all Txs
 - SetOrderInitGenesis - sets the order of the genesis file

### Step Eight
 - SetInitChainer - perform init genesis functionality for modules
 - SetBeginBlocker - perform begin block functionality for modules
 - SetEndBlocker - perform end block functionality for modules
