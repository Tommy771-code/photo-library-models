# Photo Library models

The AI model files that the Photo Library desktop app downloads on demand (reading text, searching by description,
recognising people, describing photos, place names). This repository holds no photos and no app code: only a
description of the models, their licences, and, as release files, the models themselves.

Your photos never leave your PC. The app only downloads models from here; nothing about your library is sent back.

## Where the files are

The model files are **release assets**, not files in the git tree.

- One release per pack revision. The tag is `<pack id>-<revision>`, for example `faces-2026-11-06`.
- Each model file is one asset of that release. Assets have no folders, so the folders of the file's path are joined
  with `__`: `retinaface-r50/LICENSE.txt` is the asset `retinaface-r50__LICENSE.txt`.
- Download address: `https://github.com/Tommy771-code/photo-library-models/releases/download/<tag>/<asset>`
- A released revision is never changed or overwritten. A changed model is a new revision with a new tag; old releases
  stay.
- Every release carries the `LICENSE.txt` of each model folder in it.

`MODELS.md` is the readable list of every pack, release and file with its size and sha256. `models.json` is the same
list for programs (schema 1).

## How the app checks a download

The app knows the expected size and sha256 of every file. A pack is installed only when every file matches;
otherwise nothing is installed and the app says so.

To check a file by hand, compare its sha256 with the value in `MODELS.md`:

    certutil -hashfile <file> SHA256        (Windows)
    sha256sum <file>                        (Linux, macOS: shasum -a 256 <file>)

## Licences

Each model keeps the licence of its authors. The texts, with the upstream source each names, are in
`LICENSES/<model folder>/`, and every release carries them as assets beside the model files. The table of model folders,
packs and licences is in `MODELS.md` (generated from the app's model list).

**Status of the `faces` pack:** its licence status is marked `R58-pending` in the app's list. The licence review for
this pack is still open, so treat it as pending review until that is settled.

**AuraFace mean face.** `LICENSES/auraface-r100/` also holds the notice and photo credits for the AuraFace mean face (an
average of several hundred face embeddings from COCO photos under CC BY 2.0). That file is published only with a faces
revision that uses it.
