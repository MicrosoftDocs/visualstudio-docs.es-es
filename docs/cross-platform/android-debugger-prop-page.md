---
title: Propiedades del depurador de Android (C++) | Microsoft Docs
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: a296ea142b13b9bdcda888a7f382de9eeb17a40a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="android-debugger-properties"></a>Propiedades del depurador de Android

Propiedad | Descripción | Opciones
--- | ---| ---
Tipo de depurador | Especifica qué tipo de código se va a depurar. | **Solo nativo**<br>**Solo Java**<br>
Destino de depuración | Especifica el emulador o dispositivo que se usará para la depuración. Si no se ejecutan emuladores, use "Android Virtual Device (AVD) Manager" para iniciar un dispositivo.
Paquete que se iniciará | Especifica la ubicación del .apk que se va a depurar. Elija esta opción para especificar que se debe iniciar un paquete (APK) específico cuando se depure la aplicación.
Actividad de inicio | La actividad de Android que se usará para iniciar la aplicación tiene que coincidir con la que se usa en el manifiesto. Presione Aplicar para recuperar la lista de AndroidManifest.xml y rellenarla de forma dinámica.
Rutas de búsqueda de símbolos adicionales | Ruta de búsqueda adicional para los símbolos de depuración.
Rutas de búsqueda de código fuente Java adicionales | Rutas de búsqueda adicional para los archivos de código fuente Java. Solo se aplica cuando el tipo de depurador es únicamente Java.
