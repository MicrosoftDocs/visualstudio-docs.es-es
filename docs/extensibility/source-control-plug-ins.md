---
title: Complementos de control de código fuente ( Source Control Plug-ins) Microsoft Docs
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
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699888"
---
# <a name="source-control-plug-ins"></a>Complementos de control de código fuente
La sección de referencia del SDK de complemento de Control de código [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]fuente contiene la especificación de interfaz completa que permite integrar los sistemas de control de código fuente con . Especifica la sintaxis y la semántica de las distintas funciones y tipos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] datos que el complemento de control de código fuente debe implementar para interactuar con el entorno de desarrollo integrado (IDE).

## <a name="in-this-section"></a>En esta sección
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md) Enumera las funciones que debe implementar el complemento de control de código fuente para cumplir con la API de complemento de Control de código fuente.

- Funciones de devolución de [llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Describe las funciones que el complemento de control de código fuente utiliza para devolver información al IDE mientras se ejecutan determinados comandos.

- [Enumeradores](../extensibility/enumerators.md) Enumera los tipos de datos del enumerador en la API de complemento de Control de código fuente que el complemento de control de código fuente debe conocer.

- [Banderas de capacidad](../extensibility/capability-flags.md) Describe las `SCC_CAP_xxx` marcas, que indican las capacidades de un proveedor.

- [Bitflags utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) Enumera los indicadores que son útiles en el contexto de comandos concretos.

- [Códigos de error](../extensibility/error-codes.md) Enumera los valores de `SCCTRN`error comunes devueltos por las funciones como .

- [Cadenas utilizadas como claves para encontrar un complemento](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) de control de código fuente Describe las claves para tener acceso al registro para buscar el complemento de control de código fuente.

- [MSSCCPRJ. Archivo SCC](../extensibility/mssccprj-scc-file.md) Describe un archivo del lado cliente que contiene información opaca para el IDE, pero que usa el complemento de control de código fuente para buscar la solución o el proyecto en el control de versiones.

- [Prácticas recomendadas para implementar un complemento de control de código](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) fuente Proporciona una colección de recordatorios técnicos importantes para recordar mientras implementa la API de complemento de Control de código fuente.

- [Restricciones en longitudes](../extensibility/restrictions-on-string-lengths.md) de cuerda Describe las limitaciones de la API de complemento de Control de código fuente en las longitudes de cadenas utilizadas en varias funciones.

- [Glosario](../extensibility/source-control-plug-in-glossary.md) Proporciona términos útiles y sus definiciones para leer la documentación del SDK de complemento de Control de código fuente.

- [Cómo: Desactivar advertencias](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) de compatibilidad para complementos de Control de código fuente Describe cómo deshabilitar las advertencias.

## <a name="related-sections"></a>Secciones relacionadas
- [Ejemplo de plug-in de control de](https://www.microsoft.com/download/details.aspx?id=55984) código fuente Proporciona un ejemplo de funcionalidad de complemento de control de código fuente.

- [Guía de prueba para complementos de control de](../extensibility/internals/test-guide-for-source-control-plug-ins.md) código fuente Describe los procedimientos de prueba relacionados con un complemento de control de código fuente.

- [Creación de un complemento de control de](../extensibility/internals/creating-a-source-control-plug-in.md) código fuente Describe cómo crear un complemento de control de código fuente que proporciona [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funcionalidad de control de código fuente mientras se usa la interfaz de usuario (UI) del control de código fuente.

- [Referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md) Presenta una lista de temas de referencia.
