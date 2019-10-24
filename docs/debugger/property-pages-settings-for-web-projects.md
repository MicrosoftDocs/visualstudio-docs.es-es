---
title: Configuración de propiedades para proyectos Web | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7daa58004b118d46a8248428e9a9d242dfccef8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730596"
---
# <a name="property-pages-settings-for-web-projects"></a>Configuración de páginas de propiedades para proyectos web
Se pueden cambiar los valores de las propiedades para una configuración de depuración de sitio Web en el cuadro de diálogo **Páginas de propiedades**, como se describe en [Configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). En las siguientes tablas se muestra dónde encontrar los valores relacionados con el depurador en el cuadro de diálogo **Páginas de propiedades**.

### <a name="start-options-category"></a>Categoría de opciones de inicio

| **Configuración** | **Descripción** |
| - | - |
| **Acción de inicio** | Encabezado que agrupa las opciones relacionadas con el inicio de la aplicación. |
| **Usar página actual** | Especifica la página actual como punto inicial para la depuración. |
| **Página específica:** | Especifica la página Web donde desea iniciar la depuración. |
| **Iniciar programa externo:** | Especifica el comando para iniciar el programa que desea depurar. |
| **Argumentos de la línea de comandos:** | Especifica los argumentos del comando especificado arriba. |
| **Directorio de trabajo:** | Especifica el directorio de trabajo del programa que se depura. En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación: \bin\debug de forma predeterminada. |
| **Dirección URL de inicio** | Especifica la ubicación de la aplicación Web que desea depurar. |
| **No abra una página. Esperar una solicitud de una aplicación externa** | Indica que espere una solicitud de una aplicación externa. Esta opción no inicia Internet Explorer u otra aplicación. Simplemente se prepara para la depuración cuando la llama una aplicación. |
| **Servidor** | Encabezado que agrupa las opciones relacionadas con el servidor que se va a utilizar. |
| **Usar servidor web predeterminado** | Indica que se utilice el servidor web predeterminado. |
| **Usar servidor personalizado** | Permite especificar la dirección URL base que se utilizará como servidor. |
| **Depuradores** | Encabezado que agrupa las opciones relacionadas con el tipo de depuración que se realizará. |
| **Depuración ASP.NET** | Habilita la depuración de páginas de servidor escritas para la plataforma de desarrollo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Debe especificar una dirección URL en **Dirección URL de inicio**. |
| **Depuración de código nativo** | Permite depurar llamadas a código nativo Win32 (no administrado) desde una aplicación administrada. |
| **Depuración de SQL Server** | Permite depurar objetos de la base de datos de SQL Server. |
| **Depuración de Silverlight** | Permite la depuración de los componentes de Silverlight. |

## <a name="see-also"></a>Vea también
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)