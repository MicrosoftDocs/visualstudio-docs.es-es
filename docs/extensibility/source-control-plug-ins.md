---
title: Complementos de Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3395275938d78178f6f39ccd0f67dca01194bcc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140221"
---
# <a name="source-control-plug-ins"></a>Complementos de Control de código fuente
La sección de referencia de SDK de complemento de Control de código fuente contiene la especificación de interfaz completa que permite a los sistemas de control de origen que se integra con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Especifica la sintaxis y semántica de los distintos tipos de funciones y datos que debe implementar el complemento de control de código fuente para comunicarse con el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE).  
  
## <a name="in-this-section"></a>En esta sección  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)  
 Enumera las funciones que deben implementarse mediante el complemento de control de código fuente para cumplir con la API de complementos de Control de código fuente.  
  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Describe las funciones que el complemento de control de código fuente que se usa para pasar información hacia el IDE mientras se ejecutan determinados comandos.  
  
 [Enumeradores](../extensibility/enumerators.md)  
 Enumera los tipos de datos de enumerador en la API de complementos de Control de código fuente que debe conocer el complemento de control de código fuente.  
  
 [Marcadores de capacidad](../extensibility/capability-flags.md)  
 Describe la `SCC_CAP_xxx` marcas que se indican las funciones del proveedor.  
  
 [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)  
 Marcas de listas que son útiles en el contexto de comandos concretos.  
  
 [Códigos de error](../extensibility/error-codes.md)  
 Enumera los valores de error comunes devueltos por las funciones como `SCCTRN`.  
  
 [Cadenas utilizadas como claves para buscar un complemento de control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Describe las claves para tener acceso al registro para buscar el control de código fuente complemento.  
  
 [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Describe un archivo de cliente que contiene información opaco para el IDE, pero que se usa por el complemento de control de código fuente para buscar la solución o proyecto bajo control de versiones.  
  
 [Procedimientos recomendados para implementar un complemento de control de código fuente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Proporciona una colección de recordatorios técnicas importantes recordar mientras implementa la API de complementos de Control de código fuente.  
  
 [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)  
 Describe las limitaciones de la API de complementos de Control de código fuente en las longitudes de cadenas que se usan en distintas funciones.  
  
 [Glosario](../extensibility/source-control-plug-in-glossary.md)  
 Proporciona términos útiles y sus definiciones para leer la documentación del SDK de complemento de Control de código fuente.  
  
 [Desactivación de advertencias de compatibilidad para complementos de control de código fuente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Describe cómo deshabilitar las advertencias.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ejemplo de complemento de Control de código fuente](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Proporciona un ejemplo de la funcionalidad de complemento de control de código fuente.  
  
 [Guía de pruebas para los complementos de control de código fuente](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Describe procedimientos pruebas relacionadas con un complemento de control de código fuente.  
  
 [Creación de un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Describe cómo crear un complemento de control de código fuente que proporciona funcionalidad de control de código fuente mientras esté usando el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente (UI).  
  
 [Referencia de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Presenta una lista de temas de referencia.