---
title: "Configuraci&#243;n de p&#225;ginas de propiedades para proyectos web | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "compilaciones de depuración, configuración del proyecto"
  - "configuraciones de depuración, proyectos web"
  - "depurar [Visual Studio], aplicaciones web"
  - "depurar aplicaciones web, configuración del proyecto"
  - "configuración de proyectos [Visual Studio], configuraciones de depuración"
  - "proyectos [Visual Studio], configuraciones de depuración"
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configuraci&#243;n de p&#225;ginas de propiedades para proyectos web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se pueden cambiar los valores de las propiedades para una configuración de depuración de sitio Web en el cuadro de diálogo **Páginas de propiedades**, como se describe en [Configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  En las siguientes tablas se muestra dónde encontrar los valores relacionados con el depurador en el cuadro de diálogo **Páginas de propiedades**.  
  
### Carpeta Propiedades de configuración \(categoría Opciones de inicio\)  
  
|**Valor**|**Descripción**|  
|---------------|---------------------|  
|**Acción de inicio**|Encabezado que agrupa las opciones relacionadas con el inicio de la aplicación.|  
|**Usar página actual**|Especifica la página actual como punto inicial para la depuración.|  
|**Página específica:**|Especifica la página Web donde desea iniciar la depuración.|  
|**Iniciar programa externo:**|Especifica el comando para iniciar el programa que desea depurar.|  
|**Argumentos de la línea de comandos:**|Especifica los argumentos del comando especificado arriba.|  
|**Directorio de trabajo:**|Especifica el directorio de trabajo del programa que se depura.  En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación: \\bin\\debug de forma predeterminada.|  
|**Dirección URL de inicio**|Especifica la ubicación de la aplicación Web que desea depurar.|  
|**No abrir una página.  Esperar solicitud de una aplicación externa**|Indica que espere una solicitud de una aplicación externa.  Esta opción no inicia Internet Explorer u otra aplicación.  Simplemente se prepara para la depuración cuando la llama una aplicación.|  
|**Servidor**|Encabezado que agrupa las opciones relacionadas con el servidor que se va a utilizar.|  
|**Usar servidor web predeterminado**|Indica que se utilice el servidor web predeterminado.|  
|**Usar servidor personalizado**|Permite especificar la dirección URL base que se utilizará como servidor.|  
|**Depuradores**|Encabezado que agrupa las opciones relacionadas con el tipo de depuración que se realizará.|  
|**Depuración ASP.NET**|Habilita la depuración de páginas de servidor escritas para la plataforma de desarrollo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Debe especificar una dirección URL en **Dirección URL de inicio**.|  
|**Depuración de código nativo**|Permite depurar llamadas a código nativo \(sin administrar\) Win32 desde una aplicación administrada.|  
|**Depuración de SQL Server**|Permite la depuración de objetos de base de datos de SQL Server.|  
|**Depuración de Silverlight**|Permite la depuración de los componentes de Silverlight.|  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)