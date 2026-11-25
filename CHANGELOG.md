# Check Links – changelog

## v1.13.0 (loader 1.2.0) – 25 Nov 2026
- Asks before updating: when Check Links opens and a new version is on GitHub, a window shows what's new and offers Update now / Later / Skip this version. Nothing is installed without your OK.
- "Check for updates" link at the bottom right of the window, and "Update log" to see every check and install.
- After an update, close the window and click Check Links again – no Revit restart.
- Needs this setup once (new loader); after that updates come from inside the add-in.

## v1.12.0 (loader 1.1.0) – 25 Nov 2026
- Cleaner window in the Segregation Manager colours: summary tiles (models read, links, Overlay, Attachment, failed), live status per model while checking, tree icons, settings folded away, and a Show/Hide log button.

## v1.11.0 (loader 1.1.0) – 24 Nov 2026
- No pasting or dragging: when a check finishes, the Segregation Manager website opens and picks up the results by itself, then asks which project to update or whether to create a new one (website v1.37+). The results are offered only on this PC (127.0.0.1), with a one-time code, for 10 minutes.

## v1.10.0 (loader 1.1.0) – 24 Nov 2026
- Automatic updates from GitHub: new versions download in the background and are used at the next click (no setup needed).
- Opens your hosted Segregation Manager (ibrahimhassansm-lgtm.github.io/model-segregation-manager) instead of the Claude one. The address can be changed under Options › App.

## v1.9.0 (loader 1.0.0) – 23 Nov 2026
- "The host model failed to open" no longer stops or slows the batch:
  - Each ACC model gets up to 3 tries: open; wait 5 s and open again; move that model's local cache copy aside (moved to CollaborationCache_CheckLinks_backup, never deleted) and open again after 10 s.
  - If all 3 fail the model is marked "Could not open (Revit: host model failed to open)" with the number of tries, and the batch carries on.
  - Revit warnings raised while a model opens are dismissed automatically; Revit dialogs were already answered.
  - A short pause (about 2.5 s) between models.
  - Models already open in Revit are read without opening them again, and their cache is never touched.
- "Retry failed models (N)" appears after a run with failures; it tries only those models again and merges them into the same report.
- Report: the names of all models in the ACC folder (accModels), so the Segregation Manager shows planned models that do not exist yet as "Not on ACC yet";
  "attempts" per model; models that are not on ACC yet are marked "Not on ACC yet" (notOnAcc) instead of failing.

## v1.8.1 (loader 1.0.0) – 22 Nov 2026
- Back to reading only the selected models and the models linked into them (the v1.8.0 option that also read unlinked models in the same folders is removed).

## v1.8.0 (loader 1.0.0) – 22 Nov 2026
- Models nothing links are read too: after following all links, Check Links also reads every other model in the same folders as the models it read – e.g. the ARC and INT sheet models (option "Also check models nothing links", on by default).

## v1.7.0 (loader 1.0.0) – 22 Nov 2026
- When a check finishes, the Segregation Manager opens together with the results folder, link_report.json already selected: drag it onto the app page (Segregation Manager v1.25+) and choose the project. No pasting.

## v1.6.1 (loader 1.0.0) – 22 Nov 2026
- Wording: the Segregation Manager now has an "Add Check Links results" button (no Ctrl+V needed).

## v1.6.0 (loader 1.0.0) – 22 Nov 2026
- Only ACC worksharing models: links to local / network files are left out of the results and not followed (option "Only ACC worksharing models", on by default). The log says how many were left out per model.
- Works with Segregation Manager v1.22: Ctrl+V asks whether to update an existing project or create a new one; units and pods get the Unit / Pod model type.

## v1.5.1 (loader 1.0.0) – 22 Nov 2026
- An ACC model that fails to open ("The host model failed to open. Please try again.") is retried once after 5 s before it is marked failed.

## v1.5.0 (loader 1.0.0) – 22 Nov 2026
- Every model is opened only once: models are matched by their ACC ID (then by name), so a model linked into many models, or linked several times as copies, is read once and reused.
- A model linked several times into the same host counts as one link ("Model.rvt : 2", "Model (2).rvt" are the same model).
- Models already read in this Revit session are reused, not opened again (tick "Open again models already read in this Revit session" to force a fresh read).

## v1.4.1 (loader 1.0.0) – 22 Nov 2026
- Fix: ACC models failed with "Detach option is not valid for cloud model". Revit cannot detach cloud models, so they now open normally with all worksets closed and close without saving or syncing; nothing changes on ACC.
- If your local copy of a model has unsynced work, Check Links keeps it (Revit's default would discard it).

## v1.4.0 (loader 1.0.0) – 22 Nov 2026
- New window in the Smart Linker style: your Desktop Connector ACCDocs folder (or any folder) as a tree on the left with checkboxes, search by name, "Hide archive / backup folders", and the models to check on the right.
- Tick single models or whole folders; Remove / Clear in the list; the button shows how many models will be checked.
- ACC model IDs are read straight from each model's Desktop Connector file (like Smart Linker), so no model has to be open in Revit. Also read from Revit's local cloud cache and from the open model's links.
- When a check finishes, the results are copied and the Segregation Manager opens: press Ctrl+V on its Register to add the models and links in one step ("Send to Segregation Manager" does it again any time).
- Kept: follow linked models all the way down, report, log + Excel export.

## v1.3.0 (loader 1.0.0) – 22 Nov 2026
- After each run the log is saved as <report>_log.txt and the results as <report>.xlsx next to the report.
- The workbook has three sheets: Models (status, overlay / attachment counts, found as a link in, note), Links (host model, linked model, Overlay / Attachment) and Log.
- "Export log + Excel…" saves both anywhere and opens the workbook.

## v1.2.0 (loader 1.0.0) – 22 Nov 2026
- Follows links: after reading a model, Check Links also opens every model linked into it and reads its links (Overlay or Attachment), all the way down. Each model is read once, so link loops stop. On by default ("Also check the linked models").
- The report lists the linked models too, with the model they were found in.

## v1.1.0 (loader 1.0.0) – 22 Nov 2026
- Give it a folder: Check Links scans it (and its subfolders) for every .rvt model, skipping backups (name.0001.rvt) and backup/temp folders.
- Local and network models open from their files (workshared ones detached with worksets closed).
- Desktop Connector (ACC) folders: the models are opened from ACC by their cloud ID, never from the Desktop Connector copy.
- Reports are saved in Documents\Check Links, so nothing is written into the project or ACC folder.

## v1.0.1 (loader 1.0.0) – 22 Nov 2026
- Works without a plan file: lists the open model and its links straight away, with their ACC IDs read from the links, and ticks them ready to check.
- Region is taken from the open model (AM10 is US); the old EMEA default made no sense for US projects.
- Model IDs from the open model are saved as soon as the window opens.

## v1.0.0 (loader 1.0.0) – 22 Nov 2026
- First release for Revit 2023–2027 (2023/2024 on .NET 4.8, 2025–2027 on .NET 8).
- I.H BIM Tools tab › Model Segregation › Check Links (works from Revit Home too).
- Loads the link plan JSON exported from the Model Segregation Manager (v1.16+).
- Opens each ACC model in the background: all worksets closed, detached, never synchronised, closed without saving.
- Reads every top-level Revit link: name, key, Overlay/Attachment, linked model ID; nested links skipped.
- Model IDs come from the open model and from the links of each model it opens; saved on this PC; an IDs file (JSON or CSV) can be loaded.
- Progress, Cancel and log; a model that fails to open is logged and the batch carries on.
- Writes link_report.json next to the plan, for "Import link report" in the app.
