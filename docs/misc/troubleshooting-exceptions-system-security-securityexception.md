---
title: "Soluci&#243;n de problemas de excepciones: System.Security.SecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSecurity"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "System.Security.SecurityException (clase)"
  - "SecurityException (clase)"
ms.assetid: 7679ef74-dd15-439f-bfeb-0fb45f8b2373
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Security.SecurityException
Cuando se detecta un error de seguridad, se produce una excepción <xref:System.Security.SecurityException>.  
  
## Sugerencias asociadas  
 En la página de propiedades, ajuste el nivel de permiso del ensamblado.  
 Para obtener más información, consulta <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.SqlPermissionLevel%2A>.  
  
 Almacene los datos de la aplicación en un almacenamiento aislado.  
 El almacenamiento aislado es un mecanismo de almacenamiento de datos que proporciona aislamiento y seguridad mediante la definición de modos estándar de asociar código a los datos guardados. Para obtener más información, [Almacenamiento aislado](../Topic/Isolated%20Storage.md).  
  
 Si utiliza <xref:System.Windows.Forms.OpenFileDialog>, use el método <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> para abrir o guardar un archivo.  
 Esto permite que la aplicación se ejecute en una situación que no es de plena confianza.  
  
 Asegúrese de que la aplicación lee y escribe en los registros de eventos existentes en el equipo local.  
 Es posible que la aplicación no tenga los permisos necesarios para crear inicios de sesión ni para escribir en equipos no locales.  
  
 Si llama a bibliotecas no administradas, utilice bibliotecas administradas equivalentes.  
 Es posible que exista una API equivalente en Framework. Para obtener más información, consulta [Solución de problemas de interoperabilidad](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability).  
  
 Utilice ventanas seguras.  
 La enumeración <xref:System.Security.Permissions.UIPermissionWindow> especifica el tipo de ventanas que el código tiene permitido utilizar.  
  
 Permita a los usuarios imprimir a través del componente <xref:System.Windows.Forms.PrintDialog>.  
 Esto permite que la aplicación se ejecute en una situación que no es de plena confianza. Para obtener más información, consulta <xref:System.Windows.Forms.PrintDialog>.  
  
 Imprima en la impresora predeterminada.  
 Esto permite que la aplicación se ejecute en una situación que no es de plena confianza. Es posible que intente tener acceso a una impresora para la cual no tiene derechos.  
  
 Recupere los datos del mismo servidor Web desde el que se llevó a cabo la implementación.  
 Esto permite que la aplicación se ejecute en una situación que no es de plena confianza.  
  
 Cuando implemente una solución de Office, asegúrese de que cumple todos los requisitos de seguridad.  
 Para obtener más información, vea [Consideraciones de seguridad específicas para soluciones de Office](/office-dev/office-dev/specific-security-considerations-for-office-solutions).  
  
 Si un ensamblado que implementa el objeto de seguridad personalizado hace referencia a otros ensamblados, agregue los ensamblados a los que hace referencia a la lista de ensamblados de plena confianza.  
 Para obtener más información, consulta [Caspol.exe \(Code Access Security Policy Tool\)](../Topic/Caspol.exe%20\(Code%20Access%20Security%20Policy%20Tool\).md).  
  
## Vea también  
 <xref:System.Security.SecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)