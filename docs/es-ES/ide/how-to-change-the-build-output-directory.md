---
title: 'Cómo: Cambiar el directorio de salida de compilación | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1e60ed79adf8a7b0ff2f2d66d0773c85398dea8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-change-the-build-output-directory"></a>Cómo: Cambiar el directorio de salida de compilación
Puede especificar la ubicación de salida por configuración (para debug, release o ambos) generada por el proyecto.  
  
> [!NOTE]
>  Si tiene un proyecto **Setup**, vea la nota que se proporciona al final de este artículo.  
  
## <a name="change-the-build-output-directory"></a>Cambiar el directorio de salida de compilación  
  
#### <a name="to-change-the-build-output-directory"></a>Para cambiar el directorio de salida de compilación  
  
1.  En la barra de menús, seleccione **Proyecto** > **<Appname>Propiedades**. En el **Explorador de soluciones** , también puede hacer clic con el botón secundario en el nodo del proyecto y seleccionar **Propiedades**.  
  
2.  Si tiene un proyecto de Visual Basic, seleccione la pestaña **Compilar** . Si tiene un proyecto de C#, seleccione la pestaña **Compilar**. Si tiene un proyecto de C++ o JavaScript, seleccione la pestaña **General** .  
  
3.  En la lista desplegable de configuración de la parte superior, elija la configuración cuya ubicación de archivo de resultados desea cambiar (debug, release o todas).  
  
     Busque la entrada de la ruta de acceso de la salida (**Ruta de acceso de salida de la compilación** en Visual Basic, **Directorio de salida** en Visual C++ y **Ruta de acceso de salida** en JavaScript y C#). Especifique un nuevo directorio de resultados de la compilación relativo al directorio del proyecto.  
  
> [!NOTE]
>  En un proyecto Setup, el cuadro **Nombre del archivo de salida** cambia solo la ubicación del archivo *Setup.exe*, no la ubicación de los archivos del proyecto. Para obtener más información, vea **Compilación, Propiedades de configuración, Propiedades del proyecto de implementación (cuadro de diálogo)**.  
  
## <a name="see-also"></a>Vea también  
 [Página Compilar, Diseñador de proyectos (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Página de propiedades General (Proyecto)](/cpp/ide/general-property-page-project)   
 [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)