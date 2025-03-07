# populate-release-notes-images

Tekton task to populate the releaseNotes.content.images key in the data.json file. It will update the data.json
in place so that downstream tasks relying on the releaseNotes data can use it.

## Parameters

| Name         | Description                                                          | Optional | Default value |
|--------------|----------------------------------------------------------------------|----------|---------------|
| dataPath     | Path to the JSON string of the merged data to update                 | No       | -             |
| snapshotPath | Path to the JSON string of the mapped Snapshot in the data workspace | No       | -             |

## Changes in 2.2.0
* Updated to use the `rh-registry-repo` key from the snapshot JSON for constructing 
  the image repository path, instead of relying on the data field. This change 
  ensures that the task correctly references the internal Red Hat registry format.
* Removed the use of the `translate-delivery-repo` script as the task now directly 
  accesses the `rh-registry-repo` value from the snapshot JSON.

## Changes in 2.1.0
* Updated the base image used in this task

## Changes in 2.0.0
* The `commonTags` parameter was removed in favor of the component tags in the snapshot spec file

## Changes in 1.4.0
* Updated the base image used in this task

## Changes in 1.3.0
* Updated the base image used in this task

## Changes in 1.2.1
* Fix the format and values of the images inside the resulting advisory data

## Changes in 1.2.0
* The task now looks for tags in each component of the snapshot spec file and uses them instead of the commonTags if
  any exist

## Changes in 1.1.0
* Existing CVE data is present in the resulting releaseNotes key instead of overwritten
* Update task image for fix in get-image-architectures script
  * util now outputs compact json

## Changes in 1.0.2
* Absorb change in refactored get-image-architectures script

## Changes in 1.0.1
* Update task image and make changes to accomodate for new `translate-delivery-repo` funtionality

## Changes in 1.0.0
* Task renamed from extract-release-notes-images to populate-release-notes-images

## Changes in 0.1.1
* Temp data file is stored in /tmp/ to work around permission issues in the container
