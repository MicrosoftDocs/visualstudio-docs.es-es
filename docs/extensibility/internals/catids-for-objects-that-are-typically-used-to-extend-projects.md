---
title: "CATID para los objetos que se utilizan normalmente para extender proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, CATID"
  - "GUID, VSPackages"
  - "CATID para VSPackages"
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# CATID para los objetos que se utilizan normalmente para extender proyectos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tabla siguiente se enumeran CATIDs que se utiliza para mejorar `Project` y objetos de automatización de `ProjectItem` para [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], y los proyectos de[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .  Este CATIDs se define en VSLangProj.olb.  
  
## lista de CATIDs  
  
|Name|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614\-D0D5\-11D2\-8599\-006097 C68 E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615\-D0D5\-11D2\-8599\-006097 C68 E81}|  
  
## Visual Basic CATIDs  
 La tabla siguiente se enumeran CATIDs que se utiliza para mejorar los objetos de examen de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  son todos definido en VSLangProj.olb.  
  
|Name|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FD C879 C32 A\-4751\-A3D3\-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11\-14EB\-489b\-87F0\-F01 C52 AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D\-3 C72 \-40A5\-95A0\-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932D C619 \-2EAA\-4192\-B7E6\-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812\-8191\-4e81\-B7B3\-174045AB0 CB5}|  
  
## Visual c\# CATIDs  
 El CATIDs siguiente se puede utilizar para extender los objetos de examen de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .  son todos definido en VSLangProj.olb.  
  
|Name|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003\-DE95\-4d60\-96B0\-212979F2A857}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12 CE10 A\-227F\-4963\-ADB6\-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF\-ED4E\-48B0\-8 C7 b C74 EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278\-054A\-45DB\-BF9E\-5F22484 CC84 C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8\- C855 \-4a4e\-95A5\- CB45 C67 D6 C27}|  
  
## C\+\+ CATIDs  
 El sistema siguiente CATIDs de proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] no se expone en bibliotecas de tipos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 y tiene que estar incluido en el código siempre que desee extender estos objetos del proyecto.  Este CATIDs se incluirá en las bibliotecas de tipos en versiones posteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Name|GUID|  
|----------|----------|  
|`CVCProjectNode`|{EE8299CB\-19B6\-4f20\-ABEA\-E1FD9A33B683}|  
|`CVCFolderNode`|{EE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683}|  
|`CVCFileNode`|{EE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
  
 El ejemplo de código siguiente muestra cómo programar este CATIDs en el código.  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 El sistema siguiente CATIDs de proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tampoco se expone en las bibliotecas de tipos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 y tiene que estar incluido en el código siempre que desee extender estos objetos del proyecto.  Este CATIDs solo está disponible en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 y no estará disponible en versiones posteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Name|GUID|  
|----------|----------|  
|`CVCAssemblyReferenceNode` **:**|{FE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE\-20A7\-48e4\-A CA1 \-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3\- C60 A\-44f4\-A74B\-14 C90 EF9CACE}|  
|`CVCReferences`|{FE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683}|  
  
 El ejemplo de código siguiente muestra cómo programar este CATIDs en el código:  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 El GUID para los tipos de proyecto de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] se muestra en la tabla siguiente.  
  
|Tipo de proyecto|GUID|  
|----------------------|----------|  
|[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]|{FAE04E C0 \-301F\-11D3\-BF4B\-00 C04 F79EFBC}|  
|[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]|{F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F}|  
  
## Vea también  
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)