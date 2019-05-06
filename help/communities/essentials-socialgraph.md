---
title: Social Graph Essentials
seo-title: Social Graph Essentials
description: follow component and following component overview
seo-description: follow component and following component overview
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
---

# Social Graph Essentials{#social-graph-essentials}

The ability for a Community member to follow [activities](/help/communities/essentials-activities.md) as well as be followed is established through two components:

The `follow`component must be associated with another resource, and this association is already established for existing Communities members and features in a [community site](/help/communities/overview.md#communitiessites).

The `following`component lists the members that are either following the current member or are being followed by the current member. This social graph of the relationships between members is included in the user profile established for a community site.

## Essentials for Client-Side {#essentials-for-client-side}

### Following {#following}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/socialgraph/components/hbs/relationships</td> 
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>includable</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.socialgraph</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>see <a href="/help/communities/socialgraph.md">Using Social Graph</a></td> 
  </tr>
  <tr>
   <td style="vertical-align: top;"><strong> optional<br /> property</strong></td> 
   <td>
    <ul> 
     <li>Name: <strong><code>outgoing</code></strong></li> 
     <li>Type: Boolean</li> 
     <li>Value:<br /> 
      <ul> 
       <li><i>true </i>- the <code>following</code> component will list the members who the currently signed-in member <code>follows</code></li> 
       <li><i>false </i>- the <code>following</code> component will list the members who <code>follow </code>the currently signed-in member</li> 
      </ul> </li> 
    </ul> <p>Defaults to <i>true</i> if the property is missing. Currently, it is not possible to set this property using the edit dialog in author mode. The property must be added to an instance of the <code>following </code>node using <a href="/help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>.</p> </td> 
  </tr>
 </tbody>
</table>

### Follow {#follow}

|  **resourceType** |social/socialgraph/components/hbs/following |
|---|---|
|  [**includable**](/help/communities/scf.md#add-or-include-a-communities-component) |No |
|  **templates** | /libs/social/socialgraph/components/hbs/following/following.hbs |
|  **css** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [Client-side Customizations](/help/communities/client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [Social Graph API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Social Graph Endpoints](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Server-side Customizations](/help/communities/server-customize.md)
