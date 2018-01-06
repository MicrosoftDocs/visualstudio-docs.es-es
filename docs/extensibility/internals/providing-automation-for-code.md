---
title: "Proporcionar Automation para código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e59f3826cbb2ed83510cd98209b4c83f9278397d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="providing-automation-for-code"></a>Proporcionar Automation para código
No es necesario crear un modelo de automatización para el código. El SDK de entorno no proporciona un ejemplo para hacerlo. Para obtener información sobre los modelos de código, vea la <xref:EnvDTE.CodeModel> objeto.  
  
 Para implementar un modelo de código, debe implementar las interfaces que dependen de la estructura de datos interna. Los objetos se deben derivar de la `IDispatch` clase.  
  
 Los objetos que extienden, <xref:EnvDTE.CodeModel> y <xref:EnvDTE.FileCodeModel>, están disponibles en la <xref:EnvDTE.Project> del objeto y el siguiente aspecto:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Puede elegir implementar simplemente el `CodeModel` o `FileCodeModel` interfaz en el objeto devuelto desde el `Project` y <xref:EnvDTE.ProjectItem> objetos. Proporciona funcionalidad de esta interfaz que sea adecuada para el sistema del proyecto.  
  
 Si desea agregar características, como métodos o propiedades, que no están disponibles en el estándar `CodeModel` y `FileCodeModel` interfaces, crear su propia interfaz que hereda de la norma. Asegúrese de documentar con el sistema del proyecto para que los usuarios finales sepan para buscarlo. Devuelve la interfaz estándar, pero el usuario puede llamar a la `QueryInterface` método o la conversión a la interfaz si se sabe que existe.  
  
## <a name="see-also"></a>Vea también  
 [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)