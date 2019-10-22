---
title: Los complementos de Control de origen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01e7a0ca8a509d430a0794a2cedb4b2e9d869585
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331823"
---
# <a name="source-control-plug-ins"></a>Complementos de control de código fuente
La sección de referencia de SDK de complemento de Control de código fuente contiene la especificación de interfaz completa que permite a los sistemas de control de origen que se integra con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Especifica la sintaxis y semántica de los distintos tipos de datos y funciones que debe implementar el complemento de control de código fuente para interactuar con el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE).

## <a name="in-this-section"></a>En esta sección
- [Funciones de API de complemento de Control de origen](../extensibility/source-control-plug-in-api-functions.md) enumera las funciones que deben implementarse mediante el complemento de control de código fuente con el fin de cumplir con la API de complemento de Control de código fuente.

- [Las funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md) describe funciones que el complemento de control de código fuente que se utiliza para pasar información de vuelta en el IDE mientras se ejecutan algunos comandos.

- [Los enumeradores](../extensibility/enumerators.md) enumera los tipos de datos de enumerador en la API de complemento de Control de origen que debe conocer el complemento de control de código fuente.

- [Marcadores de capacidad](../extensibility/capability-flags.md) describe la `SCC_CAP_xxx` marcas, que se indican las capacidades del proveedor.

- [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) enumera las marcas que son útiles en el contexto de comandos concretos.

- [Códigos de error](../extensibility/error-codes.md) se enumeran los valores de error comunes devueltos por las funciones como `SCCTRN`.

- [Las cadenas se usa como claves para buscar un complemento de Control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) describe las teclas de acceso del registro para buscar el control de código fuente complemento.

- [MSSCCPRJ. Archivo de SCC](../extensibility/mssccprj-scc-file.md) describe un archivo de cliente que contiene información opaca para el IDE, pero que está usando el complemento de control de código fuente para buscar la solución o proyecto bajo control de versiones.

- [Procedimientos recomendados para implementar un complemento de Control de código fuente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) proporciona una colección de recordatorios técnicas importante recordar mientras implementa la API de complemento de Control de código fuente.

- [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md) describe las limitaciones en la API de complemento de Control de código fuente en las longitudes de cadenas usadas en distintas funciones.

- [Glosario](../extensibility/source-control-plug-in-glossary.md) proporciona términos útiles y sus definiciones para leer la documentación del SDK de complemento de Control de origen.

- [Cómo: Activar desactivar advertencias de compatibilidad para complementos de Control de código fuente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) se describe cómo deshabilitar las advertencias.

## <a name="related-sections"></a>Secciones relacionadas
- [Ejemplo de complemento de Control de origen](https://www.microsoft.com/download/details.aspx?id=55984) proporciona un ejemplo de la funcionalidad de complemento de control de código fuente.

- [Guía de pruebas para los complementos de Control de código fuente](../extensibility/internals/test-guide-for-source-control-plug-ins.md) se describen los procedimientos de pruebas relacionadas con un complemento de control de código fuente.

- [Crear un complemento de Control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md) se describe cómo crear un complemento de control de origen que proporciona funcionalidad de control de código fuente mientras se está utilizando el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente (UI).

- [Referencia de SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md) presenta una lista de temas de referencia.