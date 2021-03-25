---
title: Compatibilidad con Ngen en VSIX V3 | Microsoft Docs
description: Aprenda a habilitar el generador de imágenes nativas, que es una herramienta que los desarrolladores de extensiones pueden usar para mejorar el rendimiento de las aplicaciones administradas.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0f8de3b662875a4af0423930eecfdd77e4e05b08
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090595"
---
# <a name="ngen-support-in-vsix-v3"></a>Compatibilidad con Ngen en VSIX v3

Con Visual Studio 2017 y el nuevo formato de manifiesto de extensión VSIX V3 (versión 3), los desarrolladores de extensiones ahora pueden "Ngen" sus ensamblados en el momento de la instalación.

A continuación se muestra un extracto de MSDN que explica lo que hace "Ngen":

>El generador de imágenes nativas (*Ngen.exe*) es una herramienta que mejora el rendimiento de las aplicaciones administradas. *Ngen.exe* crea imágenes nativas, que son archivos que contienen código máquina compilado específico del procesador, y las instala en la memoria caché de imágenes nativas del equipo local. El runtime puede usar imágenes nativas de la memoria caché en lugar de usar el compilador Just-In-Time (JIT) para compilar el ensamblado original.
>
>desde [Ngen.exe (generador de imágenes nativas)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Para "Ngen" un ensamblado, VSIX debe estar instalado "por instancia por equipo". Para habilitarlo, active la casilla "todos los usuarios" en el `extension.vsixmanifest` Diseñador:

![comprobar todos los usuarios](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Cómo habilitar Ngen

Para habilitar Ngen para un ensamblado, puede usar la ventana **propiedades** de Visual Studio.

Hay 4 propiedades que se pueden establecer:

1. **Ngen** (booleano): si es true, el instalador de Visual Studio "Ngen" el ensamblado.
2. **Aplicación Ngen** (cadena): Ngen proporciona la oportunidad de usar el archivo de *app.config* de una aplicación para resolver las dependencias de ensamblado. Este valor debe establecerse en una aplicación cuyo *app.config* desee usar (en relación con el directorio de instalación de Visual Studio).
3. **Arquitectura Ngen** (enum): la arquitectura para compilar el ensamblado de forma nativa. Las opciones son: a. NotSpecified b. C x86. X64 d. Todo
4. **Prioridad Ngen** (entero entre 1 y 3): el nivel de prioridad de Ngen se documenta en [Ngen.exe niveles de prioridad](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

A continuación se muestra la ventana **propiedades** en acción:

![Ngen en propiedades](media/ngen-in-properties.png)

Esto agregará metadatos a la referencia del proyecto en el archivo *. csproj* del Proyecto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Puede editar el archivo. csproj directamente, si lo prefiere.

## <a name="extra-information"></a>Información adicional

Los cambios del diseñador de propiedades se aplican a más que solo las referencias del proyecto; también puede establecer los metadatos de Ngen para los elementos dentro del proyecto (con los mismos métodos descritos anteriormente) siempre que los elementos sean ensamblados .NET.
