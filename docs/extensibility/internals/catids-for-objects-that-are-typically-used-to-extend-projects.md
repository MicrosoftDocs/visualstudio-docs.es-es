---
title: CATID para los objetos que se suelen usar para ampliar proyectos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734751492a1024507684922b760c647e91f5df15
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643631"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATID para los objetos que se suelen usar para ampliar proyectos
En la tabla siguiente se enumera CATID que se utiliza para extender `Project` y `ProjectItem` los objetos de automatización para [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], y [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos. Estos CATID se define en *VSLangProj.olb*.

## <a name="listing-of-catids"></a>Lista de CATID

|nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>CATID de Visual Basic
 En la tabla siguiente se enumera CATID que se utiliza para extender [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] examinar objetos. Se definen en *VSLangProj.olb*.

|nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>CATID de Visual C#
 El CATID siguiente puede usarse para ampliar [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] examinar objetos. Se definen en *VSLangProj.olb*.

|nombre|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>CATID de C++
 La siguiente [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] CATID no se expone en las bibliotecas de tipos en el sistema de proyectos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 y debe incluirse en el código cada vez que desee ampliar estos objetos de proyecto. Estos CATID se incluirán en las bibliotecas de tipos en las versiones posteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|nombre|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 En el ejemplo de código siguiente se muestra cómo programar estos CATID en el código.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 La siguiente [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] CATID no también se expone en las bibliotecas de tipos en el sistema de proyectos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 y debe incluirse en el código cada vez que desee ampliar estos objetos de proyecto. Estos CATID solo está disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 y no estará disponible en las versiones posteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|nombre|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 El siguiente ejemplo de código muestra cómo programar estos CATID en el código:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Los GUID de la [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos de proyecto se muestran en la tabla siguiente.


| Tipo de proyecto | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Vea también
- [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Registrar las plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)