---
title: "Complementos de Control de c&#243;digo fuente | Microsoft Docs"
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
  - "control de código fuente plug-ins, referencia"
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Complementos de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La sección de referencia de SDK de complemento de Control de código fuente contiene la especificación de interfaz completa que permite a los sistemas de control de origen que se integra con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Especifica la sintaxis y semántica de los distintos tipos de funciones y datos que se debe implementar el complemento de control de código fuente para interactuar con el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado \(IDE\).  
  
## En esta sección  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)  
 Enumera las funciones que deben ser implementadas por el complemento de control de código fuente con el fin de cumplir con la API de complementos de Control de código fuente.  
  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Describe las funciones que el complemento de control de código fuente que se utiliza para pasar información hacia el IDE mientras se ejecutan algunos comandos.  
  
 [Enumeradores](../extensibility/enumerators.md)  
 Enumera los tipos de datos de enumerador en la API de complementos de Control de código fuente que debe conocer el complemento de control de código fuente.  
  
 [Marcadores de capacidad](../extensibility/capability-flags.md)  
 Describe la `SCC_CAP_xxx` marcas, que se indican las capacidades de un proveedor.  
  
 [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)  
 Marcas de listas que son útiles en el contexto de los comandos.  
  
 [Códigos de error](../extensibility/error-codes.md)  
 Enumera los valores de error comunes devueltos por las funciones como `SCCTRN`.  
  
 [Cadenas que se utilizan como claves para buscar un Control de origen de complemento](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Describe las teclas de acceso del registro para encontrar el control de código fuente complemento.  
  
 [MSSCCPRJ. Archivo de control de código fuente](../extensibility/mssccprj-scc-file.md)  
 Describe un archivo que contiene información opaca para el IDE, pero que se utiliza el complemento de control de origen para buscar la solución o proyecto bajo control de versiones de cliente.  
  
 [Procedimientos recomendados para implementar un complemento de Control de código fuente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Proporciona una colección de recordatorios técnicas importantes que recordar cuando se implementa la API de complementos de Control de código fuente.  
  
 [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)  
 Describe las limitaciones de la API de complementos de Control de código fuente en las longitudes de cadenas usadas en distintas funciones.  
  
 [Glosario](../extensibility/source-control-plug-in-glossary.md)  
 Proporciona términos útiles y sus definiciones para leer la documentación del SDK de complemento de Control de origen.  
  
 [Cómo: desactivar las advertencias de compatibilidad para complementos de Control de código fuente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Describe cómo deshabilitar las advertencias.  
  
## Secciones relacionadas  
 [Source Control Plug\-in Sample](http://msdn.microsoft.com/es-es/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Proporciona un ejemplo de funcionalidad de complemento de control de código fuente.  
  
 [Guía de pruebas para los complementos de Control de código fuente](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Describe los procedimientos de pruebas relacionadas con un complemento de control de código fuente.  
  
 [Creación de un Control de origen de complemento](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Describe cómo crear un complemento de control de código fuente que proporciona funcionalidad de control de código fuente mientras se utiliza el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente \(UI\).  
  
 [Referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Presenta una lista de temas de referencia.