---
title: Migrar de registro de clases COM de depurador de 64 bits | Documentos de Microsoft
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 19ce2d4cc1ff92240529f35f42845778ded49fdf
ms.lasthandoff: 03/07/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrar el registro de clase COM del depurador de 64 bits

Para las extensiones del depurador que registrar clases COM en HKEY_CLASSES_ROOT (utilizando regasm, regsvr32, o escribir directamente en el registro) y cargan en msvsmon.exe (el depurador remoto), es posible proporcionar este registro para msvsmon sin necesidad de escribir en HKEY_CLASSES_ROOT. Esto afecta a los evaluadores de expresión de depurador .NET heredadas o motores de depuración que se configuran para cargar en el proceso de msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>definición de msvsmon comclass

Para utilizar esta técnica, agregue un archivo *.msvsmon-comclass-def.json junto a msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Este es un archivo de definición de comclass de msvsmon de ejemplo que registra uno administrado y una clase nativa:

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

