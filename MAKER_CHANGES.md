# Wallpaper Maker changes (on top of arclant/Loomview, Apache-2.0)

New files (app/src/main/...):
- assets/maker/template.html            renderer page (layers, clock, depth effect)
- java/com/loomview/app/maker/ProjectModel.kt, ProjectStore.kt, WallpaperApplier.kt
- java/com/loomview/app/ui/home/HomeActivity.kt
- java/com/loomview/app/ui/maker/EditorActivity.kt, EditorViewModel.kt, EditorScreen.kt,
  ProjectsActivity.kt, ProjectsViewModel.kt, ProjectsScreen.kt, MakerTheme.kt

Modified files:
- AndroidManifest.xml   HomeActivity is now the launcher; Editor/Projects activities added;
                        BrowserActivity kept (reached from "HTML Library")
- java/com/loomview/app/wallpaper/LoomviewLiveWallpaper.kt
                        added onOffsetsChanged() only (forwards home-screen swipe to maker pages)

Everything else is unchanged. Not built or tested on a device when this was written.
