---
title: "Soluci&#243;n de problemas de excepciones: System.BadImageFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "BadImageFormatException (clase)"
ms.assetid: 8d2b385a-3d6d-4dfa-8546-7ece562867e3
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.BadImageFormatException
Cuando la imagen de archivo de una DLL o de un programa ejecutable no es válida, se produce una excepción <xref:System.BadImageFormatException>.  
  
## Sugerencias asociadas  
 **Si la aplicación usa componentes de 32 bits, compruebe que siempre se ejecuta como una aplicación de 32 bits.**  
 Si la propiedad **Destino de la plataforma** del proyecto de aplicación se establece en `AnyCPU`, la aplicación compilada se puede ejecutar en el modo de 64 o 32 bits. Cuando se ejecuta como una aplicación de 64 bits, el compilador Just\-In\-Time \(JIT\) genera código nativo de 64 bits. Si la aplicación depende de un componente administrado o no administrado de 32 bits, dicho componente no se cargará en el modo de 64 bits. Para resolver este problema, establezca la propiedad **Destino de la plataforma** del proyecto en `x86` y vuelva a compilarlo.  
  
 **Compruebe que no está usando un componente que fue creado con una versión diferente de .NET Framework.**  
 Esta excepción se produce cuando una aplicación o componente desarrollado mediante [!INCLUDE[net_v10_short](../misc/includes/net_v10_short_md.md)] o [!INCLUDE[net_v11_short](../misc/includes/net_v11_short_md.md)] intenta cargar un ensamblado desarrollado mediante [!INCLUDE[net_v20SP1_short](../misc/includes/net_v20sp1_short_md.md)] o posterior, o cuando una aplicación desarrollada mediante [!INCLUDE[net_v20SP1_short](../misc/includes/net_v20sp1_short_md.md)] o [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)] intenta cargar un ensamblado desarrollado mediante [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]. La excepción <xref:System.BadImageFormatException> se puede notificar como un error en tiempo de compilación, o la excepción puede producirse en tiempo de ejecución. Vea la clase <xref:System.BadImageFormatException> si necesita un ejemplo.  
  
 **Asegúrese de que la imagen del archivo es un ensamblado o módulo administrado válido.**  
 Esta excepción se produce cuando una biblioteca de vínculos dinámicos o un ejecutable no administrado se pasa al método <xref:System.Reflection.Assembly.Load%2A> para su carga.  
  
 Para obtener más información, los usuarios de Visual Basic pueden consultar [Solución de problemas de interoperabilidad](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability).  
  
## Comentarios  
 Esta excepción se puede producir al reflejar en archivos ejecutables de C\+\+. Lo más probable es que se deba a que el compilador de C\+\+ ha eliminado las direcciones de reubicación o la sección .Reloc del archivo ejecutable. Para conservar la dirección de reubicación en un archivo ejecutable de C\+\+, especifique **\/fixed:no** al vincular.  
  
 Para conocer más causas de esta excepción, vea la clase <xref:System.BadImageFormatException>.  
  
## Vea también  
 <xref:System.BadImageFormatException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)