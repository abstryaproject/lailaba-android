Lailaba Android AAPT resource-linking fix

Why the build failed:
Android requires android:description in accessibility-service XML to point to a string resource, not contain literal text.

Apply:
1. In the GitHub repository abstryaproject/lailaba-android, replace:
   app/src/main/res/xml/accessibility_service_config.xml
   with the matching file in this patch.
2. Add:
   app/src/main/res/values/strings.xml
   from this patch. If strings.xml already exists, merge the accessibility_service_description string into its existing <resources> element rather than overwriting existing strings.
3. Commit/push to main. The Codemagic workflow triggers on pushes to main.
4. Open Codemagic and verify the new build. The fix addresses the exact AAPT error shown; it does not guarantee there are no later build errors.
