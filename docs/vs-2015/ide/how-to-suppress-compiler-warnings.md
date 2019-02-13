---
title: Procedimiento Suprimir advertencias del compilador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90a5624997a3f2a6719ccd174abee39798f1c488
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782092"
---
# <a name="how-to-suppress-compiler-warnings"></a>Cómo: Suprimir advertencias del compilador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para no saturar un registro de compilación, especifique las clases de advertencias del compilador que no desea incluir. Por ejemplo, puede usar esta técnica de revisar parte pero no toda la información que se genera automáticamente cuando se establece el nivel de detalle del registro de compilación en Normal, Detallado o Diagnóstico. Para obtener más información sobre el nivel de detalle, vea [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Para suprimir advertencias específicas de Visual C# o F#  
  
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
  
1. En el **Explorador de soluciones**, elija el proyecto en el que quiere suprimir las advertencias.  
  
2. En la barra de menús, elija **Proyecto**, **Descargar proyecto**.  
  
3. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, después, **Editar**_NombreDelProyecto_**.vbproj**.  
  
    El archivo de proyecto se abre en el editor de código.  
  
4. Busque el elemento `<NoWarn></NoWarn>` en la configuración de compilación con la que está compilando.  
  
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
  
5. Agregue uno o más números de advertencia como el valor del elemento `<NoWarn>`. Si especifica varios números de advertencia, deberá separarlos con una coma, como se muestra en el ejemplo siguiente.  
  
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
  
6. Guarde los cambios en el archivo .vbproj.  
  
7. En la barra de menús, elija **Proyecto**, **Recargar proyecto**.  
  
8. En la barra de menús, elija **Compilación**, **Recompilar solución**.  
  
    La ventana **Salida** ya no muestra las advertencias que ha especificado.  
  
   Para obtener más información, vea [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Compilar una aplicación](../ide/walkthrough-building-an-application.md)   
 [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Compilar y generar en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)
