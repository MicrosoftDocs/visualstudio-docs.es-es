---
title: Configuración de compilación avanzada (Cuadro de diálogo, C#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f3d62f6cd393dfccdaeb9047bac4780546f0087
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811982"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Configuración de compilación avanzada (Cuadro de diálogo, C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Use el cuadro de diálogo **Configuración de compilación avanzada** del **Diseñador de proyectos** para especificar las propiedades de configuración de compilación avanzada del proyecto. Este cuadro de diálogo solo se aplica a proyectos de [!INCLUDE[csprcs](../../includes/csprcs-md.md)].  
  
## <a name="general"></a>General  
 Las opciones siguientes le permiten establecer la configuración avanzada general.  
  
 **Versión de lenguaje**  
 Especifica la versión del idioma que se va a usar. El conjunto de características es diferente en cada versión, por lo que esta opción se puede usar para forzar al compilador a que permita solo un subconjunto de las características implementadas, o para habilitar solo las características compatibles con un estándar existente. Esta configuración tiene las siguientes opciones:  
  
- **ISO-1**  
  
   Se dirige a las características estándar de ISO-1.  
  
- **default**  
  
   Se dirige a la versión actual.  
  
  Para obtener más información, consulte [/langversion (Opciones del compilador de C#)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).  
  
  **Informe de errores internos del compilador**  
  Especifica si se deben notificar los errores del compilador a Microsoft. Si se establece en **aviso** (valor predeterminado), recibirá un aviso si se produce un error interno del compilador, lo que le ofrece la opción de enviar electrónicamente un informe de errores a Microsoft. Si se establece en **enviar**, se enviará automáticamente un informe de errores. Si se establece en **cola**, se pondrán en cola los informes de errores. Si se establece en **ninguno**, el error se notificará solo en la salida de texto del compilador. Para obtener más información, consulte [/errorreport (Opciones del compilador de C#)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).  
  
  **Comprobar el desbordamiento y subdesbordamiento aritmético**  
  Especifica si una instrucción aritmética de enteros que no está en el ámbito de las palabras clave [checked](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) o [unchecked](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) y que produce un valor fuera del intervalo del tipo de datos provocará una excepción en tiempo de ejecución. Para obtener más información, consulte [/checked (Opciones del compilador de C#)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).  
  
  **No hacer referencia a mscorlib.dll**  
  Especifica si se importará mscorlib.dll al programa, definiendo la totalidad <xref:System> espacio de nombres. Active esta casilla si quiere definir o crear sus propios objetos y espacios de nombres <xref:System>. Para obtener más información, consulte [/nostdlib (Opciones del compilador de C#)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).  
  
## <a name="output"></a>Salida  
 Las opciones siguientes le permiten especificar opciones de salida avanzadas.  
  
 **Información de depuración**  
 Especifica el tipo de información de depuración generado por el compilador. Para obtener información sobre cómo configurar el rendimiento de depuración de una aplicación, consulte [Facilitar la depuración de una imagen](http://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Esta configuración tiene las siguientes opciones:  
  
- **none**  
  
   Especifica que no se generará ninguna información de depuración  
  
- **full**  
  
   Permite asociar un depurador al programa en ejecución.  
  
- **pdbonly**  
  
   Permite depurar el código fuente cuando el programa se inicia en el depurador, pero solo mostrará el ensamblador cuando el programa que se ejecuta está asociado al depurador.  
  
  Para obtener más información, consulte [/debug (Opciones del compilador de C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).  
  
  **Alineación de archivo**  
  Especifica el tamaño de las secciones del archivo de salida. Los valores válidos son **512**, **1024**, **2048**, **4096** y **8192**. Estos valores se miden en bytes. Cada sección se alineará en un límite que es un múltiplo de este valor, lo que afecta al tamaño del archivo de salida. Para obtener más información, consulte [/filealign (Opciones del compilador de C#)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).  
  
  **Dirección base del archivo DLL**  
  Especifica la dirección base preferida para cargar una DLL. La dirección base predeterminada para un archivo DLL se establece mediante [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime. Para obtener más información, consulte [/baseaddress (Opciones del compilador de C#)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador de C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)   
 [Página Compilar (Diseñador de proyectos) (C#)](../../ide/reference/build-page-project-designer-csharp.md)



