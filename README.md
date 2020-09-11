# GitVersion Action

A GitHub Action to use [Git Version](https://github.com/GitTools/GitVersion) as part of an automated pipeline.

This action supports generating outputs with the corresponding values generated by GitVersion.

## GitHub Action Runner OS

 - Ubuntu 16.04.4 LTS

## GitHub Action Runner Dependencies

 - [gitversion-ubuntu.16.04-x64-5.3.7](https://github.com/GitTools/GitVersion/releases/download/5.3.7/gitversion-ubuntu.16.04-x64-5.3.7.tar.gz)

## Action Output Parameters

| Parameter       | Description                              |
| --------------- | :--------------------------------------- |
 | GitVersion_Major | Major |
 | GitVersion_Minor | Minor |
 | GitVersion_Patch | Patch |
 | GitVersion_PreReleaseTag | PreReleaseTag |
 | GitVersion_PreReleaseTagWithDash | PreReleaseTagWithDash |
 | GitVersion_PreReleaseLabel | PreReleaseLabel |
 | GitVersion_PreReleaseNumber | PreReleaseNumber |
 | GitVersion_WeightedPreReleaseNumber | WeightedPreReleaseNumber |
 | GitVersion_BuildMetaData | BuildMetaData |
 | GitVersion_BuildMetaDataPadded | BuildMetaDataPadded |
 | GitVersion_FullBuildMetaData | FullBuildMetaData |
 | GitVersion_MajorMinorPatch | MajorMinorPatch |
 | GitVersion_SemVer | SemVer |
 | GitVersion_LegacySemVer | LegacySemVer |
 | GitVersion_LegacySemVerPadded | LegacySemVerPadded |
 | GitVersion_AssemblySemVer | AssemblySemVer |
 | GitVersion_AssemblySemFileVer | AssemblySemFileVer |
 | GitVersion_FullSemVer | FullSemVer |
 | GitVersion_InformationalVersion | InformationalVersion |
 | GitVersion_BranchName | BranchName |
 | GitVersion_EscapedBranchName | EscapedBranchName |
 | GitVersion_Sha | Sha |
 | GitVersion_ShortSha | ShortSha |
 | GitVersion_NuGetVersionV2 | NuGetVersionV2 |
 | GitVersion_NuGetVersion | NuGetVersion |
 | GitVersion_NuGetPreReleaseTagV2 | NuGetPreReleaseTagV2 |
 | GitVersion_NuGetPreReleaseTag | NuGetPreReleaseTag |
 | GitVersion_VersionSourceSha | VersionSourceSha |
 | GitVersion_CommitsSinceVersionSource | CommitsSinceVersionSource |
 | GitVersion_CommitsSinceVersionSourcePadded | CommitsSinceVersionSourcePadded |
 | GitVersion_CommitDate | CommitDate |

## Sample Configuration

Use of this action requires that it be preceded by the [checkout](https://github.com/actions/checkout) action with a fetch-depth of 0. This action requires all history for all branches and tags to generate the proper semantic versioning.

### Usage
 
```yml
name: Semantic Versioning
runs-on: self-hosted
steps:
  - uses: actions/checkout@v2
    id: checkout
    with:
      fetch-depth: 0
  - name: Generate gitversion properties 
    uses: walterblacc/gitversion-action@master
    id: gitversion
  - run: |
    echo "GitVersion_SemVer: ${{steps.versioning.outputs.GitVersion_SemVer}}"
```
