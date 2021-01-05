---
title: Complementos de control de código fuente | Microsoft Docs
description: En los artículos de esta sección se describe la especificación completa de la interfaz que permite integrar los sistemas de control de código fuente con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 617b06e46bb150026f49af3e23761dfd6cb4e902
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715839"
---
# <a name="source-control-plug-ins"></a>Complementos de control de código fuente
La sección de referencia del SDK del complemento de control de código fuente contiene la especificación completa de la interfaz que permite integrar los sistemas de control de código fuente con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Especifica la sintaxis y la semántica de las distintas funciones y tipos de datos que el complemento de control de código fuente debe implementar para interactuar con el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE).

## <a name="in-this-section"></a>En esta sección
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md) Enumera las funciones que debe implementar el complemento de control de código fuente para poder cumplir con la API del complemento de control de código fuente.

- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Describe las funciones que usa el complemento de control de código fuente para devolver información al IDE mientras se ejecutan determinados comandos.

- [Enumeradores](../extensibility/enumerators.md) Enumera los tipos de datos de enumerador de la API del complemento de control de código fuente que debe conocer el complemento de control de código fuente.

- [Marcas de capacidad](../extensibility/capability-flags.md) Describe las `SCC_CAP_xxx` marcas, que indican las capacidades de un proveedor.

- [Marcadores usado por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) Muestra las marcas que son útiles en el contexto de comandos concretos.

- [Códigos de error](../extensibility/error-codes.md) Enumera los valores de error comunes devueltos por las funciones como `SCCTRN` .

- [Cadenas usadas como claves para buscar un complemento de control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Describe las claves para tener acceso al registro para buscar el complemento de control de código fuente.

- [MSSCCPRJ. El archivo SCC](../extensibility/mssccprj-scc-file.md) describe un archivo del lado cliente que contiene información opaca para el IDE, pero que usa el complemento de control de código fuente para buscar la solución o el proyecto en el control de versiones.

- [Prácticas recomendadas para implementar un complemento de control de código fuente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Proporciona una colección de recordatorios técnicos importantes que se deben recordar mientras se implementa la API del complemento de control de código fuente.

- [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md) Describe las limitaciones de la API del complemento de control de código fuente en las longitudes de las cadenas usadas en varias funciones.

- [Glosario](../extensibility/source-control-plug-in-glossary.md) Proporciona términos útiles y sus definiciones para leer la documentación del SDK del complemento de control de código fuente.

- [Desactivar advertencias de compatibilidad para complementos de control de código fuente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Describe cómo deshabilitar las advertencias.

## <a name="related-sections"></a>Secciones relacionadas
- [Ejemplo de complemento de control de código fuente](https://www.microsoft.com/download/details.aspx?id=55984) Proporciona una muestra de la funcionalidad del complemento de control de código fuente.

- [Guía de pruebas para complementos de control de código fuente](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Describe los procedimientos de prueba relacionados con un complemento de control de código fuente.

- [Crear un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md) Describe cómo crear un complemento de control de código fuente que proporciona funcionalidad de control de código fuente mientras se usa la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente (UI).

- [Referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md) Presenta una lista de temas de referencia.
