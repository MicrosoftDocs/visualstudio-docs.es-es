---
title: "Crear un Control de código fuente complemento | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 679559b70096dc7ec3baa792ea98c0c3fea7cc67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-source-control-plug-in"></a>Crear un Control de código fuente complemento
El SDK de Visual Studio proporciona recursos que permiten agregar funcionalidad de control de código fuente para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). Le permite usar cualquier archivo DLL de complemento que cumple con la API de complementos de Control de código fuente que se describen en esta documentación.  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Describe cómo instalar un complemento de control de código fuente y resalta las versiones de API de complemento de Control de código fuente está disponibles.  
  
 [Arquitectura](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Se usa un diagrama de arquitectura para explicar la integración de un control de código fuente complemento con el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Proporciona instrucciones sobre cómo probar la instalación y el funcionamiento de un complemento de control de código fuente.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Describe cómo crear un control de código fuente VSPackage que no solo proporciona funcionalidad de control de código fuente, pero reemplaza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente.  
  
 [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos de la API de complementos de Control de código fuente.  
  
 [Control de código fuente](../../extensibility/internals/source-control.md)  
 Describe las opciones para implementar el control de código fuente como una característica integrada de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].