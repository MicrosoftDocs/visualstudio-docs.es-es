---
title: Compatibilidad con Ngen en VSIX v3 | Documentos de Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15277f0a1038e43bb316d604cbc415da4a5d80bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ngen-support-in-vsix-v3"></a>Compatibilidad con Ngen en VSIX v3

Con Visual Studio de 2017 y la v3 VSIX nueva extensión (versión 3) manifiesto formato de extensión a los desarrolladores ahora pueden "ngen" los ensamblados en tiempo de instalación.

A continuación se muestra un extracto de MSDN que explica qué "ngen" hace:

>El Generador de imágenes nativas (Ngen.exe) es una herramienta que mejora el rendimiento de las aplicaciones administradas. Ngen.exe crea imágenes nativas, que son archivos que contienen código máquina compilado específicamente para un procesador, e instala estas imágenes en la memoria caché de imágenes nativas del equipo local. El runtime puede usar imágenes nativas de la memoria caché en lugar de usar el compilador Just-In-Time (JIT) para compilar el ensamblado original.
>
>desde [Ngen.exe (generador de imágenes nativas)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

En orden para "ngen" un ensamblado, la extensión VSIX debe instalarse "por instancia por equipo". Esto se puede habilitar activando la casilla de verificación "todos los usuarios" en el diseñador extension.vsixmanifest:

![Compruebe todos los usuarios](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Cómo habilitar Ngen

Para habilitar ngen para un ensamblado, puede usar el **propiedades** ventana de Visual Studio.

Hay 4 propiedades que se pueden establecer:

1. **Ngen** (booleano): si es true, el instalador de Visual Studio le "ngen" del ensamblado.
2. **Aplicación de Ngen** (cadena) Ngen proporciona la oportunidad de usar el archivo app.config de la aplicación para resolver las dependencias de ensamblado. Este valor debe establecerse en una aplicación cuyo app.config que desea usar (relativa al directorio de instalación de Visual Studio).
3. **Arquitectura de Ngen** (enumeración) - la arquitectura para compilar el ensamblado de forma nativa. Las opciones son: una. B NotSpecified. X86 c. X64 d. Todas
4. **Prioridad de Ngen** (entero entre 1 y 3) - nivel de la prioridad de Ngen se documenta en [niveles de prioridad de Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Este es un vistazo el **propiedades** ventana en acción:

![Ngen en Propiedades](media/ngen-in-properties.png)

Esto agregará los metadatos a la referencia de proyecto dentro del archivo .csproj del proyecto VSIX:

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

 >**Nota:** se puede editar el archivo .csproj directamente, si lo prefiere.

## <a name="extra-information"></a>Información adicional

Los cambios de diseñador de propiedad se aplican a algo más que las referencias de proyecto; puede establecer los metadatos de Ngen para los elementos dentro de su proyecto (con los mismos métodos que se ha descrito anteriormente) de siempre que los elementos son ensamblados .NET.