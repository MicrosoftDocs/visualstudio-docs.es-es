---
title: Provisión de automatización de código | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4adbc5385923e071e158734500e30a6a05832a1f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976224"
---
# <a name="providing-automation-for-code"></a>Provisión de automatización para código
No es necesario crear un modelo de automatización para el código. El SDK del entorno no proporciona un ejemplo para hacerlo. Para obtener información sobre los modelos de código, vea el <xref:EnvDTE.CodeModel> objeto.  
  
 Para implementar un modelo de código, debe implementar las interfaces que están determinadas por la estructura de datos interna. Los objetos que se deben derivar de la `IDispatch` clase.  
  
 Los objetos que se amplían, <xref:EnvDTE.CodeModel> y <xref:EnvDTE.FileCodeModel>, están disponibles desde el <xref:EnvDTE.Project> de objetos y el aspecto siguiente:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Puede optar por implementar simplemente el `CodeModel` o `FileCodeModel` interfaz en el objeto que se devuelve desde su `Project` y <xref:EnvDTE.ProjectItem> objetos. Proporciona funcionalidad de esta interfaz que sea adecuada para el sistema del proyecto.  
  
 Si desea agregar características, como métodos o propiedades, que no están disponibles en el estándar `CodeModel` y `FileCodeModel` interfaces, cree su propia interfaz que hereda de la norma. No olvide documentó con el sistema del proyecto para que los usuarios finales para buscar lo sepa. Devolver la interfaz estándar, pero el usuario puede llamar a la `QueryInterface` método o la conversión a la interfaz si se sabe que existe.  
  
## <a name="see-also"></a>Vea también  
 [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)