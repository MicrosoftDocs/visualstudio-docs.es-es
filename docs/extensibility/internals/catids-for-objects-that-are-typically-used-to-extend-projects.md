---
title: CATIDs para objetos que se utilizan normalmente para extender proyectos . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5754e53f24731eb44dba128ccfcf4b474e833d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709863"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATID para objetos que se utilizan normalmente para extender proyectos
En la tabla siguiente se enumeran los `Project` `ProjectItem` CATID [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] se utilizan para extender y automatizar objetos para , , y proyectos. Estos CATIDse se definen en *VSLangProj.olb*.

## <a name="listing-of-catids"></a>Listado de CATIDs

|Nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|N.o 610D4614-D0D5-11D2-8599-006097C68E81|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|N.o 610D4615-D0D5-11D2-8599-006097C68E81|

## <a name="visual-basic-catids"></a>Visual Basic CATIDs
 En la tabla siguiente se enumeran los [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] CATID que se utilizan para extender objetos de exploración. Todos ellos se definen en *VSLangProj.olb*.

|Nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|• E0FDC879-C32A-4751-A3D3-0B3824BD575F?|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|N.o 67F8DD11-14EB-489b-87F0-F01C52AF3870|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|•EA5BD05D-3C72-40A5-95A0-28A2773311CA|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|N.o 932DC619-2EAA-4192-B7E6-3D15AD31DF49|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|N.o 2289B812-8191-4e81-B7B3-174045AB0CB5|

## <a name="visual-c-catids"></a>CatID de Visual C.
 Los siguientes CATID se pueden [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] utilizar para extender objetos de exploración. Todos ellos se definen en *VSLangProj.olb*.

|Nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|N.o 4EF9F003-DE95-4d60-96B0-212979F2A857|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|A12CE10A-227F-4963-ADB6-3A43388513CA|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|N.o 8D58E6AF-ED4E-48B0-8C7B-C74EF0735451|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|N.o 914FE278-054A-45DB-BF9E-5F22484CC84C|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|N.o 2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27|

## <a name="c-catids"></a>CatIDcCCC+C++
 Los [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] siguientes CATID del sistema de proyectos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no se exponen en las bibliotecas de tipos de .NET 2003 y deben incluirse en el código siempre que desee ampliar estos objetos de proyecto. Estos CATIDs se incluirán en las bibliotecas de tipos en versiones posteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Nombre|GUID|
|----------|----------|
|`CVCProjectNode`|EE8299CB-19B6-4f20-ABEA-E1FD9A33B683?|
|`CVCFolderNode`|EE8299CA-19B6-4f20-ABEA-E1FD9A33B683?|
|`CVCFileNode`|EE8299C9-19B6-4f20-ABEA-E1FD9A33B683?|

 En el ejemplo de código siguiente se muestra cómo programar estos CATIDs en el código.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Los [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] siguientes CATID del sistema de proyectos tampoco [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se exponen en las bibliotecas de tipos de .NET 2003 y deben incluirse en el código siempre que desee extender estos objetos de proyecto. Estos CATID solo están [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] disponibles en .NET 2003 y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]no estarán disponibles en las versiones posteriores de .

|Nombre|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|•FE8299C9-19B6-4f20-ABEA-E1FD9A33B683?|
|`CVCProjectReferenceNode`|N.o 593DCFCE-20A7-48e4-ACA1-49ADE9049887?|
|`CVCActiveXReferenceNode`|N.o 9E8182D3-C60A-44f4-A74B-14C90EF9CACE|
|`CVCReferences`|•FE8299CA-19B6-4f20-ABEA-E1FD9A33B683?|

 En el ejemplo de código siguiente se muestra cómo programar estos CATIDs en el código:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Los GUID para [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] los [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos de proyecto y y se muestran en la tabla siguiente.

| Tipo de proyecto | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | •FAE04EC0-301F-11D3-BF4B-00C04F79EFBC |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | F184B08F-C81C-45F6-A57F-5ABD9991F28F |

## <a name="see-also"></a>Vea también
- [Agregar plantillas de proyecto y elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Registrar plantillas de proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)
