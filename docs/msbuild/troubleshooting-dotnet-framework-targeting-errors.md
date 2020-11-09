---
title: Solucionar problemas de versión de .NET Framework de destino | Microsoft Docs
description: Obtenga información sobre los errores de MSBuild que pueden producirse debido a problemas de referencia y cómo pueden resolverse esos errores.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 98c3ba64454ca25b62dc5dbe0964db64b010a7ec
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046979"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Solucionar problemas de versión de .NET Framework de destino

En este tema se describen los errores de MSBuild que pueden producirse debido a problemas de referencia y cómo pueden resolverse esos errores.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Ha hecho referencia a un proyecto o ensamblado que tiene como destino una versión diferente de .NET Framework

 Puede crear aplicaciones que hagan referencia a proyectos o ensamblados destinados a otras versiones de .NET Framework. Por ejemplo, puede crear una aplicación destinada al perfil de cliente de .NET Framework 4 pero que haga referencia a un ensamblado destinado a .NET Framework 2.0. Pero si crea un proyecto destinado a una versión anterior de .NET Framework, no puede establecer una referencia en ese proyecto a un proyecto o ensamblado destinado al perfil de cliente de .NET Framework 4 o al propio .NET Framework 4. Para resolver el error, asegúrese de que la aplicación tiene como destino un perfil o perfiles que sean compatibles con el perfil al que se destinan los proyectos o ensamblados a los que la aplicación hace referencia.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Ha cambiado el destino de un proyecto a una versión diferente de .NET Framework

 Si cambia la versión de destino de .NET Framework de la aplicación, Visual Studio cambia algunas de las referencias, pero es posible que deba actualizar algunas manualmente. Por ejemplo, podría producirse uno de los errores mencionados anteriormente si cambia una aplicación para que establezca como destino .NET Framework 3.5 Service Pack 1 y esa aplicación tiene recursos o valores que dependen del perfil de cliente de .NET Framework 4.

 Para corregir la configuración de la aplicación, abra el **Explorador de soluciones** , elija **Mostrar todos los archivos** y, a continuación, edite el archivo *app.config* en el editor XML de Visual Studio. Cambie la versión en la configuración para que coincida con la versión adecuada de .NET Framework. Por ejemplo, puede cambiar la configuración de la versión de 4.0.0.0 a 2.0.0.0. De igual manera, para una aplicación con recursos agregados, abra el **Explorador de soluciones** , elija el botón **Mostrar todos los archivos** , expanda **Mi proyecto** (Visual Basic) o **Propiedades** (C#) y, a continuación modifique el archivo *Resources.resx* en el editor XML de Visual Studio. Cambie la versión de 4.0.0.0 a 2.0.0.0.

 Si la aplicación tiene recursos como iconos o mapas de bits o valores como cadenas de conexión de datos, también puede resolver el error quitando todos los elementos en la página **Configuración** del **Diseñador de proyectos** y, a continuación, volver a agregar los parámetros necesarios.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Ha cambiado el destino de un proyecto a una versión diferente de .NET Framework y las referencias no se resuelven

 Si cambia el destino de un proyecto a otra versión de .NET Framework, las referencias pueden no resolverse correctamente en algunos casos. Las referencias completas explícitas a ensamblados a menudo provocan este problema, pero puede resolverlo quitando las referencias que no se resuelvan y agregándolas luego de nuevo al proyecto. También puede editar el archivo de proyecto para reemplazar las referencias. En primer lugar, quite las referencias de la forma siguiente:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 A continuación, reemplácelas por la forma simple:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Después de cerrar y volver a abrir el proyecto, también debe volver a generarlo para garantizar que todas las referencias se resuelven correctamente.

## <a name="see-also"></a>Consulte también

- [Procedimiento: Usar una versión de .NET Framework como destino](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework client profile](/dotnet/framework/deployment/client-profile) (Perfil de cliente de .NET Framework)
- [Información general sobre destinos de Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)
