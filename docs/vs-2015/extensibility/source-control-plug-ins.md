---
title: Los complementos de Control de origen | Microsoft Docs
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
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7c51efc30251a177e07b7acf3e4c62821cb9488
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745457"
---
# <a name="source-control-plug-ins"></a>Complementos de control de código fuente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La sección de referencia de SDK de complemento de Control de código fuente contiene la especificación de interfaz completa que permite a los sistemas de control de origen que se integra con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Especifica la sintaxis y semántica de los distintos tipos de datos y funciones que debe implementar el complemento de control de código fuente para interactuar con el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE).  
  
## <a name="in-this-section"></a>En esta sección  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)  
 Enumera las funciones que deben implementarse mediante el complemento de control de código fuente con el fin de cumplir con la API de complemento de Control de código fuente.  
  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Describe funciones que el complemento de control de código fuente que se utiliza para pasar información de vuelta en el IDE mientras se ejecutan algunos comandos.  
  
 [Enumeradores](../extensibility/enumerators.md)  
 Enumera los tipos de datos del enumerador en la API de complemento de Control de origen que debe conocer el complemento de control de código fuente.  
  
 [Marcadores de capacidad](../extensibility/capability-flags.md)  
 Describe el `SCC_CAP_xxx` marcadores, que se indican las capacidades del proveedor.  
  
 [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)  
 Enumera las marcas que son útiles en el contexto de comandos concretos.  
  
 [Códigos de error](../extensibility/error-codes.md)  
 Enumera los valores de error comunes devueltos por las funciones como `SCCTRN`.  
  
 [Cadenas utilizadas como claves para buscar un complemento de control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Describe las teclas de acceso del registro para buscar el control de código fuente complemento.  
  
 [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Describe un archivo de cliente que contiene información opaca para el IDE, pero que está usando el complemento de control de código fuente para buscar la solución o proyecto bajo control de versiones.  
  
 [Procedimientos recomendados para implementar un complemento de control de código fuente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Proporciona una colección de los recordatorios técnicas importante recordar mientras implementa la API de complemento de Control de código fuente.  
  
 [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)  
 Describe las limitaciones en la API de complemento de Control de código fuente en las longitudes de cadenas usadas en distintas funciones.  
  
 [Glosario](../extensibility/source-control-plug-in-glossary.md)  
 Proporciona los términos útiles y sus definiciones para leer la documentación del SDK de complemento de Control de origen.  
  
 [Desactivación de advertencias de compatibilidad para complementos de control de código fuente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Describe cómo deshabilitar las advertencias.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ejemplo de complemento de Control de código fuente](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Proporciona un ejemplo de la funcionalidad de complemento de control de código fuente.  
  
 [Guía de pruebas para los complementos de control de código fuente](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Describe los procedimientos de pruebas relacionadas con un complemento de control de código fuente.  
  
 [Creación de un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Describe cómo crear un complemento de control de origen que proporciona funcionalidad de control de código fuente mientras se está utilizando el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfaz de usuario de control de código fuente (UI).  
  
 [Referencia de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Presenta una lista de temas de referencia.

