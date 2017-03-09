---
title: "Configuraci&#243;n de compilaci&#243;n avanzada (Cuadro de di&#225;logo, C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.AdvancedBuildSettings"
helpviewer_keywords: 
  - "Opciones de compilación [C#], avanzadas"
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configuraci&#243;n de compilaci&#243;n avanzada (Cuadro de di&#225;logo, C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El cuadro de diálogo **Configuración de compilación avanzada** del **Diseñador de proyectos** se usa para especificar las propiedades de configuración de compilación avanzada del proyecto.  Este cuadro de diálogo solo se aplica a los proyectos de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  
  
## General  
 Las opciones siguientes permiten establecer la configuración avanzada general.  
  
 **Versión de lenguaje**  
 Especifica la versión del lenguaje que se va a utilizar.  El conjunto de características varía en cada versión, por lo que esta opción se puede utilizar para forzar al compilador a que permita sólo un subconjunto de las características implementadas, o a que habilite sólo aquéllas que sean compatibles con un estándar existente.  Esta configuración tiene las opciones siguientes:  
  
-   **ISO\-1**  
  
     Con destino a las características del estándar ISO\-1.  
  
-   **default**  
  
     Con destino a la versión actual.  
  
 Para obtener más información, vea [\/langversion \(Conformant Syntax\)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).  
  
 **Informe de errores del compilador interno**  
 Especifica si se enviará un informe de errores del compilador a Microsoft.  Si establece su valor en **preguntar** \(valor predeterminado\), recibirá un mensaje si se produce un error interno del compilador, en el cual se le preguntará si desea enviar electrónicamente un informe de errores a Microsoft.  Si establece su valor en **enviar**, se enviará automáticamente un informe de errores.  Si lo establece en **cola**, se pondrán en cola los informes de errores.  Si lo establece en **ninguno**, el error se notificará sólo en el texto de salida del compilador.  Para obtener más información, vea [\/errorreport \(Set Error Reporting Behavior\)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).  
  
 **Comprobar el desbordamiento y subdesbordamiento aritmético**  
 Especifica si una instrucción aritmética entera que no se encuentre dentro del ámbito de las palabras clave [checked](/dotnet/csharp/language-reference/keywords/checked) o [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) y cuyo resultado sea un valor situado fuera del intervalo del tipo de datos producirá una excepción en tiempo de ejecución. Para obtener más información, vea [\/checked \(Check Integer Arithmetic\)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).  
  
 **No hacer referencia al archivo mscorlib.dll**  
 Especifica si mscorlib.dll se importará al programa, definiendo el espacio de nombres <xref:System> completo.  Active esta casilla si desea definir o crear sus propios objetos y  espacio de nombres <xref:System>.  Para obtener más información, vea [\/nostdlib \(Do Not Import Standard Library\)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).  
  
## Output  
 Las opciones siguientes permiten especificar las opciones de salida avanzadas.  
  
 **Info. de depuración**  
 Especifica el tipo de información de depuración generada por el compilador.  Para obtener información sobre cómo configurar la depuración de una aplicación, vea [Facilitar la depuración de una imagen](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md).  Esta configuración tiene las opciones siguientes:  
  
-   **nada**  
  
     Especifica que no se generará ninguna información de depuración  
  
-   **completa**  
  
     Permite asociar un depurador al programa en ejecución.  
  
-   **pdbonly**  
  
     Permite depurar el código fuente cuando el programa se inicializa en el depurador, pero sólo se mostrará el ensamblador cuando el programa que se ejecuta está asociado al depurador.  
  
 Para obtener más información, vea [\/debug \(Emit Debugging Information\)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).  
  
 **Alineación de archivo**  
 Especifica el tamaño de las secciones del archivo de salida.  Los valores válidos son **512**, **1024**, **2048**, **4096** y **8192**.  Estos valores se miden en bytes.  Cada sección se alineará en un límite que es un múltiplo de este valor, lo que afecta al tamaño del archivo de salida.  Para obtener más información, vea [\/filealign \(Specify Section Alignment\)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).  
  
 **Dirección base del archivo DLL**  
 Especifica la dirección base preferida donde se va a cargar un archivo DLL.  La dirección base predeterminada de un archivo DLL la establece Common Language Runtime de [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)].  Para obtener más información, vea [\/baseaddress \(Specify Base Address of DLL\)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).  
  
## Vea también  
 [C\# Compiler Options](/dotnet/csharp/language-reference/compiler-options/index)   
 [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md)