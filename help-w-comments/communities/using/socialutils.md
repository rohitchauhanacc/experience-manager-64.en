---
title: SocialUtils Refactoring
seo-title: SocialUtils Refactoring
description: The package com.adobe.cq.social.ugcbase.SocialUtils was deprecated in AEM 6.1
seo-description: The package com.adobe.cq.social.ugcbase.SocialUtils was deprecated in AEM 6.1
uuid: 3def1043-9e7b-4364-b6f3-5b1294b37fe4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 922412f5-d3fe-4160-b8a6-2bab15e1e66c
index: y
internal: n
snippet: y
---

# SocialUtils Refactoring{#socialutils-refactoring}

### SocialUtils Package Deprecated {#socialutils-package-deprecated}

The package** com.adobe.cq.social.ugcbase.SocialUtils** was deprecated in AEM 6.1.

The following tables list the methods to use in place of SocialUtils methods.

### SocialResourceUtilities Package  {#socialresourceutilities-package}

| Methods in com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities |
|---|
| Boolean checkPermission(ResourceResolver resolver, String path, String action) |  |
| SocialResourceProvider getSocialResourceProvider(Resource resource) |  |
| SocialResourceConfiguration getStorageConfig(Resource resource) |  |
| Resource getUGCResource(Resource userResource) |  |
| Resource getUGCResource(Resource userResource, ResourceResolverFactory rrf) |new |
| Resource getUGCResource(Resource userResource, ResourceResolverFactory rrf, String resourceTypeHint) |new |
| Resource getUGCResource(Resource userResource, String resourceTypeHint) |  |
| boolean hasModeratePermissions(Resource resource) |  |
| String resourceToACLPath(Resource resource) |  |
| String resourceToUGCStoragePath(Resource resource) |replaces String resourceToUGCPath(Resource resource) |
| String UGCToResourcePath(Resource resource) |  |
| String UGCToResourcePath(String ugcPath) |method signature changed |
| String UGCToResourcePath(String ugcPath, ResourceResolver resolver) |new |

| Methods in `com.adobe.cq.social.`utilities.resource.api.SocialResourceUtilities |
|---|
| SocialResourceProvider getSocialResourceProvider(Resource resource) |replaces SocialResourceProvider getConfiguredProvider(Resource resource) |

### SCFUtilities Package {#scfutilities-package}

| Methods in `com.adobe.cq.social.`utilities.scf.api.SCFUtilites |
|---|
| String getAvatar(UserProperties userProperties) |
| String getAvatar(UserProperties userProperties, int size) |
| String getAvatar(UserProperties userProperties, String absoluteDefaultAvatar) |
| String getAvatar(UserProperties userProperties, String absoluteDefaultAvatar, SocialUtils.AVATAR_SIZE size) |
| Page getContainingPage(Resource resource) |
| String getSocialProfileURL(String username, ResourceResolver resolver, Page page) |
| UserProperties getUserProperties(ResourceResolver resolver, String userId) |

### For Internal Use Only {#for-internal-use-only}

| boolean canAddNode(Session session, String path) |
|---|
| String createUniqueNameHint(String message) |
| String createUniqueNameHint(String message, int numRandomChars) |
| String generateRandomString(int length) |
| SocialResourceConfiguration getDefaultStorageConfig() |
| Page getPage(String path, ResourceResolver resolver) |
| String getPagePath(Resource resource) |
| String getPagePath(String path) |
| String getResourceTypeForIncludedResource(Resource component, String defaultResourceType, String designPropertyName) |
| String getResourceTypeFromDesign(Resource resource, String styleProperty, String defaultValue) |
| boolean isResourceOwner(Resource resource) |
| String mapUGCPath(Resource resource) |
| String mapUGCPath(String ugcPath, ResourceResolver resolver) |
| boolean mayPost(ResourceResolver resolver, Resource resource) |
| String prepareUserGeneratedContent(ResourceResolver resolver, String path) |

### Methods No Longer Available {#methods-no-longer-available}

| Node createNode(ResourceResolver resolver, String path, String nodeType) |
|---|
| Resource getResourceAtPath(ResourceResolver resolver, String path) |
| Resource getResourceAtPath(ResourceResolver resolver, String path, String resourceType) |
| Configuration getStorageCloudServiceConfig(Resource resource) |
| TranslationManager getTranslationManager() |
| TranslationSaveQueue getTranslationSaveQueue() |
| boolean mayAccessUGC(ResourceResolver resolver) |
