---
title: CATID para objetos que se usan normalmente para extender proyectos
description: Obtenga información sobre los CATID de los objetos que se usan para extender los objetos de automatización Project y ProjectItem para Visual Basic, Visual C# y Visual C++ proyectos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: abc0df47c243cff4bf80ab18b15f1cbaa9526cdd
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898682"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATID para objetos que se usan normalmente para extender proyectos
En la tabla siguiente se enumeran los CATID que se usan para extender `Project` y automatizar objetos para proyectos , y `ProjectItem` [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Estos CATID se definen en *VSLangProj.olb*.

## <a name="listing-of-catids"></a>Lista de CATID

|Nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>Visual Basic CATID
 En la tabla siguiente se enumeran los CATID que se usan para extender los [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] objetos de exploración. Todos se definen en *VSLangProj.olb.*

|Nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>CATID de Visual C#
 Los siguientes CATID se pueden usar para extender los [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] objetos de exploración. Todos se definen en *VSLangProj.olb.*

|Nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>CATID de C++
 Los siguientes CATID del sistema de proyectos no se exponen en las bibliotecas de tipos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .NET 2003 y deben incluirse en el código siempre que quiera extender estos objetos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de proyecto. Estos CATID se incluirán en las bibliotecas de tipos en versiones posteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Nombre|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-MIENTOA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-TAXISA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ZOSA-E1FD9A33B683}|

 En el ejemplo de código siguiente se muestra cómo programar estos CATID en el código.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Los siguientes CATID del sistema de proyectos tampoco se exponen en las bibliotecas de tipos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .NET 2003 y deben incluirse en el código siempre que quiera extender estos objetos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de proyecto. Estos CATID solo están disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 y no estarán disponibles en las versiones posteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Nombre|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ZOSA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-MIENTOA-E1FD9A33B683}|

 En el ejemplo de código siguiente se muestra cómo programar estos CATID en el código:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Los GUID para los tipos [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] de proyecto y se muestran en la tabla [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] siguiente.

| Tipo de proyecto | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Consulta también
- [Agregar plantillas de proyecto y elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
