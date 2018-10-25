---
title: Fundamentos de la integración de Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f28781adb2679fb70e3d45d47507cd6e6aabd994
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811020"
---
# <a name="source-control-integration-essentials"></a>Conceptos básicos de la integración del control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] admite dos tipos de integración de control de código fuente: un complemento de control de origen que proporciona la funcionalidad básica y se ha creado mediante la API de complemento de Control de código fuente (conocido anteriormente como la API de MSSCCI) y una solución de integración de control de código fuente basado en un VSPackage que Proporciona una funcionalidad más sólida.  
  
## <a name="source-control-plug-in"></a>Complemento de Control de código fuente  
 Un complemento de Control de código fuente se escribe como un archivo DLL que implementa la API de complemento de Control de código fuente. Funcionalidad de integración de control de origen y de registro se proporciona a través de la API. Este enfoque es más fácil de implementar que un VSPackage de control de código fuente y usa el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la interfaz de usuario (UI) para la mayoría de las operaciones de control de código fuente.  
  
 Para implementar un complemento mediante la API de complemento de Control de código fuente de control de código fuente, siga estos pasos:  
  
1. Crear un archivo DLL que implementa las funciones especificadas en [de complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md).  
  
2. Registrar la DLL mediante la realización de las entradas del Registro adecuados, como se describe en [Cómo: instalar un complemento de Control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Crear una aplicación auxiliar de la interfaz de usuario y mostrarlo cuando se lo solicite el paquete de adaptador de Control de código fuente (el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componente que controla la funcionalidad de control de código fuente a través de los complementos de control de código fuente).  
  
   Para obtener más información, consulte [crear un complemento de Control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>VSPackage de Control de código fuente  
 Un implementación de VSPackage de control de código fuente le permite desarrollar un reemplazo personalizado para el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la interfaz de usuario de control de código fuente. Este enfoque ofrece control completo sobre la integración de control de código fuente, pero requiere que proporcionan los elementos de interfaz de usuario e implementar las interfaces del control de origen en caso contrario, se les ofrecerá en el enfoque del complemento.  
  
 Para implementar un VSPackage de control de código fuente, debe:  
  
1. Crear y registrar su propio control de código fuente VSPackage, como se describe en [registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Reemplace el control de código fuente de forma predeterminada la interfaz de usuario con la interfaz de usuario personalizada. Consulte [interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Especifique los glifos que se utilizará y controlar **el Explorador de soluciones** eventos de glifo. Consulte [glifo Control](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Controlar eventos de consulta de editar y guardar la consulta, como se muestra en [para guardar la consulta Editar consulta](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
   Para obtener más información, consulte [crear un VSPackage de Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general](../../extensibility/internals/source-control-integration-overview.md)   
 [Creación de un Control de código fuente complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)

