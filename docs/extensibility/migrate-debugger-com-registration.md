---
title: Migrar el registro de la clase de 64 bits depurador COM | Documentos de Microsoft
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: "1"
author: gregg-miskelly
ms.author: greggm
manager: ghogen
ms.workload: greggm
ms.openlocfilehash: 737c970555fce8f3cdac118421eddb09f52d7c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrar el registro de la clase COM de depurador de 64 bits

Para las extensiones del depurador que registrar clases COM en HKEY_CLASSES_ROOT (utilizando regasm, regsvr32, o escribir directamente en el registro) y se cargan en msvsmon.exe (el depurador remoto), ahora es posible proporcionar este registro a msvsmon sin necesidad de para escribir en HKEY_CLASSES_ROOT. Esto afecta a los evaluadores de expresión de depurador .NET heredados o motores de depuración que están configurados para cargar en el proceso de msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Para usar esta técnica, agregue un archivo de *.msvsmon-comclass-def.json junto a msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Este es un ejemplo de archivo de msvsmon-comclass-def que registra uno administrado y una clase nativa:

Nombre de archivo: MyCompany.MyExample.msvsmon-comclass-def.json

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
