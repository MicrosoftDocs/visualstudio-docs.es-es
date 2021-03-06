---
title: Migrar el registro de clase COM del depurador de 64 bits | Microsoft Docs
description: Obtenga información sobre cómo registrar clases COM en msvsmon para las extensiones del depurador sin escribir en HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.workload:
- greggm
ms.openlocfilehash: adc1db57de2167ff3caa0e87e1075c8ff5b462e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886722"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migración del registro de clase COM del depurador de 64 bits

En el caso de las extensiones del depurador que registran clases COM en HKEY_CLASSES_ROOT utilizando Regasm, regsvr32 o escribiendo directamente en el registro y se cargan en *msvsmon.exe* (el depurador remoto), ahora es posible proporcionar este registro a msvsmon sin necesidad de escribir en HKEY_CLASSES_ROOT. Esto afecta a los evaluadores de expresiones del depurador de .NET heredados o a los motores de depuración que se configuran para cargar en el proceso *msvsmon.exe* .

## <a name="msvsmon-comclass-def"></a>msvsmon-ComClass-Def

Para usar esta técnica, agregue un **.msvsmon-comclass-def.jsen* el archivo junto a msvsmon (INSTALLDIR:* \Common7\IDE\Remote Debugger\x64 *).

Este es un ejemplo de archivo msvsmon-ComClass-DEF que registra una clase administrada y una clase nativa:

FileName: *MyCompany.MyExample.msvsmon-comclass-def.jsen*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
