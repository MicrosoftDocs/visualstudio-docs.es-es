---
title: "Fundamentos de la integraci&#243;n del Control de c&#243;digo fuente | Microsoft Docs"
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
  - "Integración de Control de código fuente, essentials"
  - "Integración de Control de código fuente, información general"
  - "Fundamentos de la integración del Control de código fuente"
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Fundamentos de la integraci&#243;n del Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos tipos de integración del control de código fuente: un complemento de control de código fuente que proporciona la funcionalidad y se compila con Control de código fuente API de complemento \(antes conocido como el MSSCCI API\), y una solución VSPackage\-basada de integración de control de código fuente que proporciona una funcionalidad más robusta.  
  
## complemento de control de código fuente  
 Un complemento de control de código fuente se escribe como un archivo DLL que implementa el complemento de control de código fuente API.  La funcionalidad de integración de registro y de control de código fuente se proporciona con la API.  Este enfoque es más fácil de implementar que un control de código fuente VSPackage, y utiliza la interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(UI\) para la mayoría de las operaciones de control de código fuente.  
  
 Para implementar un complemento de control de código fuente utilizando el complemento de control de código fuente API, siga estos pasos:  
  
1.  Cree un archivo DLL que implementa las funciones especificadas en [Complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registre la DLL creando las entradas de Registro correspondientes, como se describe en [Cómo: instalar un complemento de Control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Cree una interfaz de usuario de la aplicación auxiliar muéstrela y cuando se le pregunte por el paquete de adaptador de control de código fuente \(el componente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que controla la funcionalidad de control de código fuente a través de complementos de control de código fuente\).  
  
 Para obtener más información, vea [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## control de código fuente VSPackage  
 Una implementación de VSPackage de control de código fuente permite desarrollar un reemplazo personalizado para la interfaz de usuario del control de código fuente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Este enfoque proporciona un control total sobre la integración del control de código fuente, pero requiere proporcionar los elementos de la interfaz de usuario e implementar las interfaces de control de código fuente que se proporcionadas de otra manera en enfoque de complemento.  
  
 Para implementar un control de código fuente VSPackage, debe:  
  
1.  Cree y registre poseen el control de código fuente VSPackage, como se describe en [Selección y registro](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Reemplace la interfaz de usuario predeterminada del control de código fuente con la interfaz de usuario personalizada.  Vea [Interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Especifique los glifos que se utilizarán, y controlar eventos de glifo de **Explorador de soluciones** .  Vea [Control de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Edición de consulta ID y eventos Save de la consulta, como se muestra en [Guardar la consulta Editar consulta](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Para obtener más información, vea [Crear un VSPackage del Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## Vea también  
 [Información general](../../extensibility/internals/source-control-integration-overview.md)   
 [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Crear un VSPackage del Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)