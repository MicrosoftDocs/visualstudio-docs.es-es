---
title: "C&#243;mo: Suprimir advertencias del compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# C&#243;mo: Suprimir advertencias del compilador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede declutter una compilación registrar especificando una o más clases de advertencias del compilador que no desea para contener.  Por ejemplo, puede utilizar esta técnica de revisar algunas pero no toda la información que se genera automáticamente cuando se establece el nivel de detalle de generación\- registro en normal, en Detailed, o Diagnostic.  Para obtener más información sobre detalle, vea [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### Para suprimir las advertencias concretas para Visual c\# o F\#  
  
1.  En **Explorador de soluciones**, elija el proyecto en el que desea suprimir advertencias.  
  
2.  En la barra de menú, elija **Vista**, **Páginas de propiedades**.  
  
3.  Elija la página **Compilación**.  
  
4.  En el cuadro **Suprimir advertencias**, especifique los códigos de error de las advertencias que desee suprimir, separados por puntos y comas, y después recompile la solución.  
  
### Para suprimir las advertencias concretas para Visual C\+\+  
  
1.  En **Explorador de soluciones**, elija el proyecto o archivo de código fuente donde desea suprimir advertencias.  
  
2.  En la barra de menú, elija **Vista**, **Páginas de propiedades**.  
  
3.  Elija la categoría **Propiedades de configuración**, elija la categoría **C\/C\+\+**, y elija la página **Opciones avanzadas**.  
  
4.  Realice uno de estos pasos:  
  
    -   En el cuadro **Deshabilitar advertencias específicas**, especifique los códigos de error de las advertencias que desee suprimir, separados por un punto y coma.  
  
    -   En el cuadro **Deshabilitar advertencias específicas**, elija **Modificar** para mostrar más opciones.  
  
5.  Elija el botón **Aceptar**, y después recompile la solución.  
  
## Supresión de las advertencias para Visual Basic  
 Puede ocultar advertencias del compilador específicas para Visual Basic editando el archivo .vbproj para el proyecto.  También puede utilizar [Página de compilación, Diseñador de proyectos](../ide/reference/compile-page-project-designer-visual-basic.md) para suprimir las advertencias por categoría.  Para obtener más información, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### Para suprimir las advertencias concretas para Visual Basic  
  
1.  En **Explorador de soluciones**, elija el proyecto en el que desea suprimir advertencias.  
  
2.  En la barra de menú, elija **proyecto**, **Descargar el proyecto**.  
  
3.  En **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación **Modificar***ProjectName***.vbproj**.  
  
     El archivo de proyecto se abre en el editor de código.  
  
4.  Busque el elemento de `<NoWarn></NoWarn>` en la configuración de compilación con la que se está compilando.  
  
     El ejemplo siguiente se muestra el elemento de `<NoWarn></NoWarn>` en texto en negrita para la configuración de compilación debug en una plataforma x86:  
  
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
        <NoWarn> </NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Agregue uno o más números de advertencia como el valor de `<NoWarn>`.  Si especifica los números de advertencia múltiples, deberá separarlas con una coma, como se muestra en el ejemplo siguiente.  
  
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
  
7.  En la barra de menú, elija **proyecto**, **Volver a cargar el proyecto**.  
  
8.  En la barra de menú, elija **Compilación**, **Recompilar solución**.  
  
     La ventana **Resultado** ya no muestra a advertencias especificado.  
  
 Para obtener más información, vea [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
## Vea también  
 [Tutorial: Compilar una aplicación](../ide/walkthrough-building-an-application.md)   
 [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)