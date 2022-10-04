# Tauri Svelte Template

## Goal

Completely separate the actual Tauri structure from the Front-end (here svelte but can be any front end).\
Also only depends on Cargo and not npm on Tauri's side.

## Steps for an existing project

If you only want to figure how to quickly do it on your own project :\
    - uninstall @tauri-apps/cli from node modules and install tauri-cli with cargo instead\
    - move the tauri-src (and rename if you want) on the same level as your previous root folder.\
    - modify the tauri.conf.json, here I used `svelte` as the front folder name. Like so :

```
"build": {
    "beforeBuildCommand": "cd ./svelte && npm run build",
    "beforeDevCommand": "cd ./svelte && npm run dev",
    "devPath": "http://localhost:5173",
    "distDir": "../svelte/build/"
},
```

**Before**

.\
└── MyProject /\
&emsp;&emsp;├── node_modules\
&emsp;&emsp;├── src\
&emsp;&emsp;├── src-tauri\
&emsp;&emsp;└── ...and so on

**After**

.\
└── MyProject/\
&emsp;&emsp;├── svelte/ (or any fitting name, but change accordingly in tauri.conf.json)\
&emsp;&emsp;│&emsp;&emsp;├── node_modules\
&emsp;&emsp;│&emsp;&emsp;├── src\
&emsp;&emsp;│&emsp;&emsp;├── src-tauri\
&emsp;&emsp;│&emsp;&emsp;└── ...and so on\
&emsp;&emsp;└── tauri/ (was tauri-src)\
&emsp;&emsp;&emsp;&emsp;&emsp;├── src\
&emsp;&emsp;&emsp;&emsp;&emsp;├── tauri.conf.json\
&emsp;&emsp;&emsp;&emsp;&emsp;└── ...and so on




## Steps for a project cloned from this repo

### Prerequisites

- See : https://tauri.app/v1/guides/getting-started/prerequisites
  - Rust
  - Node v16.14+
  
### Steps

- `cargo install tauri-cli`
- `npm install` inside the front-end directory
- You **must** change the `tauri -> bundle -> identifier` inside tauri.config.json.
- now you can run either `cargo tauri dev` or cargo `tauri build` from the tauri folder

