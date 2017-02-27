---
title: "Automatizaci&#243;n de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CodeModel (objeto)"
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Automatizaci&#243;n de c&#243;digo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

crear un modelo de automatización para el código no se requiere.  El entorno SDK no proporciona un ejemplo de ello.  Para la visión de los modelos de código, vea el objeto de <xref:EnvDTE.CodeModel> .  
  
 Para implementar un modelo de código, debe implementar las interfaces que se determina por la estructura de datos interna.  Los objetos deben derivarse de la clase de `IDispatch`.  
  
 Los objetos que se extiende, <xref:EnvDTE.CodeModel> y <xref:EnvDTE.FileCodeModel>, están disponibles en el objeto de <xref:EnvDTE.Project> , y como el siguiente:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Puede implementar simplemente `CodeModel` o la interfaz de `FileCodeModel` en el objeto que se devuelve de los objetos de `Project` y de <xref:EnvDTE.ProjectItem> .  Proporcione cualquier funcionalidad de esta interfaz apropiada para el sistema del proyecto.  
  
 Si desea agregar características, como las propiedades o métodos, que no están disponibles de `CodeModel` e interfaces estándar de `FileCodeModel` , cree poseen la interfaz que hereda de.  Asegúrese del documento en él con el sistema del proyecto para que los usuarios finales sabrán para él.  Se devuelve la interfaz estándar, pero el usuario puede llamar al método de `QueryInterface` o convertir a la interfaz si se sabe que exista.  
  
## Vea también  
 [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)