---
title: "Cómo: Suprimir advertencias del compilador | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 0c4c9c5a885b6f71b8531d4b04baecaec7f45949
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-suppress-compiler-warnings"></a>Cómo: Suprimir advertencias del compilador
Para no saturar un registro de compilación, especifique las clases de advertencias del compilador que no quiere incluir. Por ejemplo, puede usar esta técnica de revisar parte pero no toda la información que se genera automáticamente cuando se establece el nivel de detalle del registro de compilación en Normal, Detallado o Diagnóstico. Para obtener más información sobre el nivel de detalle, vea [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Para suprimir advertencias específicas de Visual C# o F# #
  
1.  En el **Explorador de soluciones**, elija el proyecto en el que quiere suprimir las advertencias.  
  
2.  En la barra de menús, elija **Ver**, **Páginas de propiedades**.  
  
3.  Seleccione la página **Compilación**.  
  
4.  En el cuadro **Suprimir advertencias**, especifique los códigos de error de las advertencias que quiere suprimir, separados por punto y coma y, después, recompile la solución.  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>Para suprimir las advertencias concretas para Visual C++  
  
1.  En el **Explorador de soluciones**, elija el proyecto o archivo de origen donde quiere suprimir advertencias.  
  
2.  En la barra de menús, elija **Ver**, **Páginas de propiedades**.  
  
3.  Elija la categoría **Propiedades de configuración**, seleccione la categoría **C/C++** y, después, seleccione la página **Opciones avanzadas**.  
  
4.  Realice uno de estos pasos:  
  
    -   En el cuadro **Deshabilitar advertencias específicas**, especifique los códigos de error de las advertencias que quiere suprimir, separados por un punto y coma.  
  
    -   En el cuadro **Deshabilitar advertencias específicas**, elija **Editar** para mostrar más opciones.  
  
5.  Elija el botón **Aceptar** y, después, recompile la solución.  
  
## <a name="suppressing-warnings-for-visual-basic"></a>Supresión de las advertencias para Visual Basic  
 Edite el archivo .vbproj del proyecto para ocultar advertencias del compilador específicas para Visual Basic. También puede usar la [Página de compilación, Diseñador de proyectos](../ide/reference/compile-page-project-designer-visual-basic.md) para suprimir las advertencias por categoría. Para obtener más información, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Para suprimir las advertencias concretas para Visual Basic  
  
1.  En el **Explorador de soluciones**, elija el proyecto en el que quiere suprimir las advertencias.  
  
2.  En la barra de menús, elija **Proyecto**, **Descargar proyecto**.  
  
3.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, después, **Editar***NombreDelProyecto***.vbproj**.  
  
     El archivo de proyecto se abre en el editor de código.  
  
4.  Busque el elemento `<NoWarn></NoWarn>` en la configuración de compilación con la que está compilando.  
  
     En el ejemplo siguiente se muestra el elemento `<NoWarn></NoWarn>` en negrita para la configuración de compilación de depuración en una plataforma x86:  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn></NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Agregue uno o más números de advertencia como el valor del elemento `<NoWarn>`. Si especifica varios números de advertencia, deberá separarlos con una coma, como se muestra en el ejemplo siguiente.  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  Guarde los cambios en el archivo .vbproj.  
  
7.  En la barra de menús, elija **Proyecto**, **Recargar proyecto**.  
  
8.  En la barra de menús, elija **Compilación**, **Recompilar solución**.  
  
     La ventana **Salida** ya no muestra las advertencias que ha especificado.  
  
 Para obtener más información, vea [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Compilar una aplicación](../ide/walkthrough-building-an-application.md)   
 [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Compilar y generar en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)

