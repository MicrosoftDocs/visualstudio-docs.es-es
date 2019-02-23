---
title: Migrar el registro de la clase COM de depurador de 64 bits | Microsoft Docs
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712208"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrar el registro de la clase COM de depurador de 64 bits

Para extensiones del depurador que COM de registrar las clases en HKEY_CLASSES_ROOT mediante regasm, regsvr32, o escribir directamente en el registro y se cargan en *msvsmon.exe* (el depurador remoto), ahora es posible que proporcionarle esta información registro de msvsmon sin necesidad de escribir en HKEY_CLASSES_ROOT. Esto afecta a los evaluadores de expresiones del depurador .NET heredados o motores de depuración que están configurados para cargar en el *msvsmon.exe* proceso.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Para usar esta técnica, agregue un  **.msvsmon-comclass-def.json* archivo junto a msvsmon (InstallDir:* \Common7\IDE\Remote Debugger\x64*).

Este es un ejemplo de archivo msvsmon-comclass-def que registra uno administrado y una clase nativa:

FileName: *MyCompany.MyExample.msvsmon-comclass-def.json*

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
