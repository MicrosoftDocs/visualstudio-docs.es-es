---
title: 'Cómo: Cambiar el directorio de resultados de compilación | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a12accc247d79a68eaafc9878dc5e9d7d8c7d6dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580016"
---
# <a name="how-to-change-the-build-output-directory"></a>Cómo: Cambiar el directorio de resultados de compilación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: cambiar el directorio de salida de compilación](https://docs.microsoft.com/visualstudio/ide/how-to-change-the-build-output-directory).  
  
Puede especificar la ubicación de salida por configuración (para debug, release o ambos) generada por el proyecto.  
  
> [!NOTE]
>  Si tiene un proyecto **Setup** , vea la nota que se proporciona al final de este artículo.  
  
## <a name="changing-the-build-output-directory"></a>Cambiar el directorio de salida de la compilación  
  
#### <a name="to-change-the-build-output-directory"></a>Para cambiar el directorio de salida de compilación  
  
1.  En la barra de menús, elija **Proyecto**, *NombreDeAplicación* **Propiedades**. En el **Explorador de soluciones** , también puede hacer clic con el botón secundario en el nodo del proyecto y seleccionar **Propiedades**.  
  
2.  Si tiene un proyecto de Visual Basic, seleccione la pestaña **Compilar** . Si tiene un proyecto de Visual C#, seleccione la pestaña **Compilar** . Si tiene un proyecto de C++ o JavaScript, seleccione la pestaña **General** .  
  
3.  En la lista desplegable de configuración de la parte superior, elija la configuración cuya ubicación de archivo de resultados desea cambiar (debug, release o todas).  
  
     Busque la entrada de la ruta de acceso de los resultados (**Ruta de acceso de los resultados de la compilación** en Visual Basic, **Directorio de resultados** en Visual C++ y **Ruta de acceso de los resultados** en JavaScript y C#). Especifique un nuevo directorio de resultados de la compilación relativo al directorio del proyecto.  
  
> [!NOTE]
>  En un proyecto Setup, el cuadro **Nombre del archivo de salida** cambia solo la ubicación del archivo Setup.exe, no la ubicación de los archivos del proyecto. Para obtener más información, vea **Compilación, Propiedades de configuración, Propiedades del proyecto de implementación (cuadro de diálogo)**.  
  
## <a name="see-also"></a>Vea también  
 [Compilar (Página, Diseñador de proyectos) (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Página de propiedades General (Proyecto)](http://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45)   
 [Compilar y generar en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)



