---
title: Soporte ngen en VSIX v3 Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702399"
---
# <a name="ngen-support-in-vsix-v3"></a>Compatibilidad con Ngen en VSIX v3

Con Visual Studio 2017 y el nuevo formato de manifiesto de extensión VSIX v3 (versión 3), los desarrolladores de extensiones ahora pueden "ngen" sus ensamblados en el momento de la instalación.

A continuación se muestra un extracto de MSDN que explica lo que hace "ngen":

>El generador de imágenes nativas (*Ngen.exe*) es una herramienta que mejora el rendimiento de las aplicaciones administradas. *Ngen.exe* crea imágenes nativas, que son archivos que contienen código de máquina específico del procesador compilado, y las instala en la caché de imágenes nativas del equipo local. El runtime puede usar imágenes nativas de la memoria caché en lugar de usar el compilador Just-In-Time (JIT) para compilar el ensamblado original.
>
>de [Ngen.exe (Generador de imágenes nativas)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Para "ngen" un ensamblaje, el VSIX debe instalarse "por instancia por máquina". Esto se puede habilitar marcando la casilla de `extension.vsixmanifest` verificación "todos los usuarios" en el diseñador:

![comprobar todos los usuarios](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Cómo habilitar Ngen

Para habilitar ngen para un ensamblado, puede usar la ventana **Propiedades** en Visual Studio.

Hay 4 propiedades que se pueden establecer:

1. **Ngen** (Boolean): si es true, el instalador de Visual Studio "ngen" el ensamblado.
2. **Aplicación Ngen** (cadena): Ngen proporciona la oportunidad de utilizar el archivo *app.config* de una aplicación para resolver las dependencias del ensamblado. Este valor debe establecerse en una aplicación cuyo *app.config* desea usar (en relación con el directorio de instalación de Visual Studio).
3. **Ngen Architecture** (enum): la arquitectura para compilar de forma nativa el ensamblado. Las opciones son: a. No especificado b. X86 c. X64 d. Todas
4. **Ngen Priority** (entero entre 1 y 3) - El nivel de prioridad de Ngen se documenta en los niveles de [prioridad Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Aquí hay un vistazo a la ventana **Propiedades** en acción:

![ngen en propiedades](media/ngen-in-properties.png)

Esto agregará metadatos a la referencia del proyecto dentro del archivo *.csproj* del proyecto VSIX:

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
> Puede editar el archivo .csproj directamente, si lo prefiere.

## <a name="extra-information"></a>Información adicional

Los cambios del diseñador de propiedades se aplican a algo más que referencias de proyecto; También puede establecer los metadatos de Ngen para los elementos dentro del proyecto (utilizando los mismos métodos descritos anteriormente) siempre que los elementos sean ensamblados .NET.
