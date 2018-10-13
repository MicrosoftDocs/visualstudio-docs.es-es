---
title: 'Cómo: Utilizar variables de entorno en una compilación | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a03b706957d6308dce90fb9f0dd2284338e7609
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294619"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Cómo: Utilizar variables de entorno al compilar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Al compilar proyectos, a menudo es necesario establecer las opciones de compilación mediante información que no está en el archivo del proyecto o en los archivos que componen el proyecto. Normalmente, esta información se almacena en variables de entorno.  
  
## <a name="referencing-environment-variables"></a>Hacer referencia a variables de entorno  
 Todas las variables de entorno están disponibles para el archivo del proyecto [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) como propiedades.  
  
> [!NOTE]
>  Si el archivo del proyecto contiene una definición explícita de una propiedad que tiene el mismo nombre que una variable de entorno, la propiedad en el archivo del proyecto invalida el valor de la variable de entorno.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Para utilizar una variable de entorno en un proyecto de MSBuild  
  
-   Haga referencia a la variable de entorno del mismo modo que lo haría con una variable declarada en el archivo del proyecto. Por ejemplo, el código siguiente hace referencia a la variable de entorno BIN_PATH:  
  
     `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
 Puede utilizar un atributo `Condition` para proporcionar un valor predeterminado a una propiedad si no se ha establecido la variable de entorno.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Para proporcionar un valor predeterminado a una propiedad  
  
-   Utilice un atributo `Condition` en una propiedad para establecer el valor solo si la propiedad no tiene ningún valor. Por ejemplo, el código siguiente establece la propiedad `ToolsPath` c:\tools solo si la variable de entorno `ToolsPath` no se establece:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Los nombres de propiedades no distinguen mayúsculas de minúsculas, por lo que `$(ToolsPath)` y `$(TOOLSPATH)` hacen referencia a la misma propiedad o variable de entorno.  
  
## <a name="example"></a>Ejemplo  
 El siguiente archivo del proyecto utiliza variables de entorno para especificar la ubicación de los directorios.  
  
```  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  

[MSBuild](msbuild.md)

[Propiedades de MSBuild](../msbuild/msbuild-properties1.md)

[Cómo: Compilar los mismos archivos de código fuente con diferentes opciones](../msbuild/how-to-build-the-same-source-files-with-different-options.md)


