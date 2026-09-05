# FakeBot status – ReHLDS 3.14.0.857

This repository builds a Linux i386 `engine_i486.so` from the exact ReHLDS tag `3.14.0.857` / commit `89958d348ea617227a4e4360b76900423527bd9e` and applies the included status patch.

## How to use

1. Create a new GitHub repository (public or private).
2. Upload everything from this ZIP, including `.github/workflows/build.yml`.
3. Open the repository on GitHub.
4. Go to **Actions**.
5. Select **Build patched ReHLDS i386**.
6. Click **Run workflow**.
7. Wait for the green check.
8. Open the completed workflow run and download the artifact named:
   `engine_i486-fakebot-status-3.14.0.857`

The artifact contains `engine_i486.so`.

## Server test

Before replacing anything on the game server:

- Stop the server.
- Make a backup of the original `engine_i486.so`.
- Upload the newly built `engine_i486.so` next to `hlds_linux`.
- Keep YaPB settings unchanged, including:
  `EnableFakeBotFeatures = 1`
  `yb_enable_fake_steamids "1"`
- Start the server and run `status`.

If the server fails to start, restore the original `engine_i486.so` backup.

## Important

This build changes only the ReHLDS status formatting path. It does not modify YaPB or Reunion.
