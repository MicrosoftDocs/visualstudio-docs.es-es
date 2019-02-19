---
title: Cuadro de diálogo Configuración de proyecto de VC++, Proyectos y soluciones, Opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d5d697cecfb30bc52f3386411a32a05718b0662
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783134"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Configuración de proyecto de VC++, Proyectos y soluciones, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Este cuadro de diálogo permite definir la configuración del proyecto de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] relacionada con el registro de compilación y los tipos de archivos auxiliares.  
  
### <a name="to-access-this-dialog-box"></a>Para obtener acceso a este cuadro de diálogo  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  Seleccione **Proyectos y soluciones** y **Configuración de proyecto de VC++**.  
  
## <a name="build-customization-search-path"></a>Ruta de búsqueda de personalizaciones de compilación  
 Especifica la lista de directorios que contienen archivos .rules, que ayudan a definir reglas de compilación para los proyectos.  
  
## <a name="build-logging"></a>Registro de compilación  
 **Sí**  
 Habilita la generación del archivo de registro de compilación. Esta opción genera BuildLog.htm, que se encuentra en el directorio de archivos intermedios del proyecto. Cada compilación nueva sobrescribe el archivo BuildLog.htm anterior.  
  
 **No**  
 Desactiva la generación del archivo de registro de compilación.  
  
## <a name="build-timing"></a>Tiempo de compilación  
 **Sí**  
 Activa el registro de compilación. Si se selecciona, se muestra en la ventana de salida el tiempo que se tarda en completar la compilación. Para más información, vea [Ventana de salida](../../ide/reference/output-window.md).  
  
 **No**  
 Desactiva el registro de compilación.  
  
## <a name="extensions-to-hide"></a>Extensiones para ocultar  
 Especifica las extensiones de nombre de archivo de los archivos que no aparecerán en el **Explorador de soluciones** cuando esté habilitada la opción **Mostrar todos los archivos**.  
  
## <a name="extensions-to-include"></a>Extensiones para incluir  
 Especifica las extensiones de nombre de archivo de los archivos que se pueden importar al proyecto.  
  
## <a name="maximum-concurrent-c-compilations"></a>Máximo de compilaciones de C++ concurrentes  
 Especifica el número máximo de núcleos de CPU que se usarán para la compilación paralela de C++.  
  
## <a name="show-environment-in-log"></a>Mostrar entorno en el registro  
 **Sí**  
 Muestra las variables de entorno en el archivo de registro de compilación. Esta opción especifica que se muestren todas las variables de entorno en el archivo de registro de compilación durante las compilaciones de proyectos de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 **No**  
 Las variables de entorno se excluyen del archivo de registro de compilación.  
  
## <a name="solution-explorer-mode"></a>Modo Explorador de soluciones  
 **Mostrar únicamente archivos del proyecto**  
 Configura el **Explorador de soluciones** de modo que solo muestre archivos del proyecto.  
  
 **Mostrar todos los archivos**  
 Configura el **Explorador de soluciones** de modo que muestre tanto archivos del proyecto como archivos del disco en la carpeta del proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Compilación de programas de C/C++](http://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008)   
 [Referencia de compilación de C/C++](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
