---
title: Configuración de los proyectos Web de páginas de propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cb7cd3f8c3678d37feb2267f68ab5d2b3d970e0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995378"
---
# <a name="property-pages-settings-for-web-projects"></a>Configuración de páginas de propiedades para proyectos web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se pueden cambiar los valores de las propiedades para una configuración de depuración de sitio Web en el cuadro de diálogo **Páginas de propiedades**, como se describe en [Configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). En las siguientes tablas se muestra dónde encontrar los valores relacionados con el depurador en el cuadro de diálogo **Páginas de propiedades**.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Carpeta Propiedades de configuración (categoría Opciones de inicio)  
  
|**Configuración**|**Descripción**|  
|-----------------|---------------------|  
|**Acción de inicio**|Encabezado que agrupa las opciones relacionadas con el inicio de la aplicación.|  
|**Usar página actual**|Especifica la página actual como punto inicial para la depuración.|  
|**Página específica:**|Especifica la página Web donde desea iniciar la depuración.|  
|**Iniciar programa externo:**|Especifica el comando para iniciar el programa que desea depurar.|  
|**Argumentos de la línea de comandos:**|Especifica los argumentos del comando especificado arriba.|  
|**Directorio de trabajo:**|Especifica el directorio de trabajo del programa que se depura. En [!INCLUDE[csprcs](../includes/csprcs-md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación: \bin\debug de forma predeterminada.|  
|**Dirección URL de inicio**|Especifica la ubicación de la aplicación Web que desea depurar.|  
|**No abra una página. Esperar solicitud de una aplicación externa**|Indica que espere una solicitud de una aplicación externa. Esta opción no inicia Internet Explorer u otra aplicación. Simplemente se prepara para la depuración cuando la llama una aplicación.|  
|**Servidor**|Encabezado que agrupa las opciones relacionadas con el servidor que se va a utilizar.|  
|**Usar servidor web predeterminado**|Indica que se utilice el servidor web predeterminado.|  
|**Usar servidor personalizado**|Permite especificar la dirección URL base que se utilizará como servidor.|  
|**Depuradores**|Encabezado que agrupa las opciones relacionadas con el tipo de depuración que se realizará.|  
|**Depuración ASP.NET**|Habilita la depuración de páginas de servidor escritas para la plataforma de desarrollo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Debe especificar una dirección URL en **Dirección URL de inicio**.|  
|**Depuración de código nativo**|Permite depurar llamadas a código nativo Win32 (no administrado) desde una aplicación administrada.|  
|**Depuración de SQL Server**|Permite depurar objetos de la base de datos de SQL Server.|  
|**Depuración de Silverlight**|Permite la depuración de los componentes de Silverlight.|  
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
