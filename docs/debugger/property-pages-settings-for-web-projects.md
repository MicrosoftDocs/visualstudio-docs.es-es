---
title: "Página de propiedades de configuración para los proyectos Web | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e58541c5ab0c7a38773740343349880aa5297e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="property-pages-settings-for-web-projects"></a>Configuración de páginas de propiedades para proyectos web
Puede cambiar los valores de propiedad para una configuración de depuración de sitio web en el **páginas de propiedades** cuadro de diálogo, como se describe en [configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). Las siguientes tablas muestran dónde encontrar valores relacionados con el depurador en el **páginas de propiedades** cuadro de diálogo.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Carpeta Propiedades de configuración (categoría Opciones de inicio)  
  
|**Configuración de**|**Descripción**|  
|-----------------|---------------------|  
|**Acción de inicio**|Encabezado que agrupa las opciones relacionadas con el inicio de la aplicación.|  
|**Utilice la página actual**|Especifica la página actual como punto inicial para la depuración.|  
|**Página específica:**|Especifica la página Web donde desea iniciar la depuración.|  
|**Iniciar programa externo:**|Especifica el comando para iniciar el programa que desea depurar.|  
|**Argumentos de línea de comandos:**|Especifica los argumentos del comando especificado arriba.|  
|**Directorio de trabajo:**|Especifica el directorio de trabajo del programa que se depura. En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación: \bin\debug de forma predeterminada.|  
|**Dirección URL de inicio**|Especifica la ubicación de la aplicación Web que desea depurar.|  
|**No abrir una página. Esperar solicitud de una aplicación externa**|Indica que espere una solicitud de una aplicación externa. Esta opción no inicia Internet Explorer u otra aplicación. Simplemente se prepara para la depuración cuando la llama una aplicación.|  
|**Servidor**|Encabezado que agrupa las opciones relacionadas con el servidor que se va a utilizar.|  
|**Usar servidor Web predeterminado**|Indica que se utilice el servidor web predeterminado.|  
|**Usar servidor personalizado**|Permite especificar la dirección URL base que se utilizará como servidor.|  
|**Depuradores**|Encabezado que agrupa las opciones relacionadas con el tipo de depuración que se realizará.|  
|**Depuración ASP.NET**|Habilita la depuración de páginas de servidor escritas para la plataforma de desarrollo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Debe especificar una dirección URL en **dirección URL de inicio**.|  
|**Depuración de código nativo**|Permite depurar llamadas a código nativo Win32 (no administrado) desde una aplicación administrada.|  
|**Depuración de SQL Server**|Permite depurar objetos de la base de datos de SQL Server.|  
|**Depuración de Silverlight**|Permite la depuración de los componentes de Silverlight.|  
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)