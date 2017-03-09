---
title: "Error de MSBuild MSB3482 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.SignFile.SignToolError"
helpviewer_keywords: 
  - "MSB3482"
ms.assetid: fd09371f-2658-4534-affa-edb485575f1a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3482
**MSB3482: Se produjo un error al firmar: '\<error\>'.**  
  
 Al publicar mediante la implementación de ClickOnce o si usa SignTool para firmar los manifiestos, puede producirse este error, generado por SignTool. Aquí se enumeran los problemas comunes.  
  
 **Se produjo un error al firmar: 'El valor no puede ser nulo. Nombre del parámetro: strongNameKey'.**  
  
 Este error puede aparecer en la lista de errores durante la implementación de ClickOnce. El problema se genera al seleccionar una clave de firma no válida. Normalmente está intentando usar una clave no cifrada con RSA. SignTool admite solo el cifrado de claves de RSA.  
  
 Para corregir este error, obtenga una clave con el cifrado de RSA que tenga habilitada la firma de código.  
  
 **Se produjo un error al firmar: 'No se pudo crear una cadena de certificados en una entidad de certificación raíz de confianza'.**  
  
 Este error puede aparecer en la lista de errores durante la implementación de ClickOnce. El problema es que el certificado tiene una cadena o entidad de certificación raíz que no es de confianza en el equipo del usuario. Esto suele ocurrir al mover los certificados y claves de un equipo a otro.  
  
 Para corregir este error, instale del "certificado raíz" de la entidad de certificación \(CA\) que lo creó. Normalmente, se puede ir al sitio web de la entidad de certificación y descargarlo de nuevo cuando sea necesario.  
  
 **Se produjo un error al firmar: 'No se pudo firmar... \\setup.exe. Error SignTool: ISignCode:: Sign devolvió un error: 0x80880253 El certificado del firmante no es válido para firmar.'**  
  
 Este error puede aparecer en la lista de errores durante la implementación de ClickOnce.  
  
 Probablemente el problema está causado porque el certificado no está dentro de las fechas válidas, por ejemplo, si tiene un certificado caducado.  
  
 Para corregir este error, obtenga un certificado actualizado que tenga una fecha válida.  
  
 Para obtener información sobre cómo actualizar el certificado, consulte el artículo 925521, "You receive an error message when you try to update a Visual Studio 2005 ClickOnce application after the certificate that was used to sign the installation expires" de Microsoft Knowledge Base en [http:\/\/support.microsoft.com](http://support.microsoft.com/kb/925521).  
  
 **El conjunto de claves no existe.**  
  
 Puede haber una discrepancia entre el archivo .pfx y el certificado. Pruebe a eliminar y volver a instalar el certificado o volver a crear el archivo pfx.  
  
 **clave no válida para usarla en el estado especificado**  
  
 Vea http:\/\/blogs.msdn.com\/b\/smondal\/archive\/2012\/05\/08\/an\-error\-occurred\-while\-signing\-key\-not\-valid\-for\-use\-in\-specified\-state.aspx  
  
 **'El parámetro es incorrecto.**  
  
 ¿Se está ejecutando la compilación en un servicio o en una cuenta de usuario diferente del que importó el certificado? Intente desactivar cualquier configuración de directiva de seguridad local que necesite protección de clave privada.  A continuación, elimine y vuelva a importar el certificado para la cuenta de usuario de la compilación.  
  
 **No se puede completar la operación solicitada.  El equipo debe ser de confianza para la delegación y la cuenta de usuario actual debe estar configurada para permitir la delegación.**  
  
 Vea [esta entrada de blog MSDN.](http://technet.microsoft.com/en-us/library/cc782684\(v=ws.10\).aspx)  
  
## Vea también  
 [Introducción a la firma de código](https://msdn.microsoft.com/en-us/library/ms537361\(v=vs.85\).aspx)   
 [SignTool.exe \(Sign Tool\)](../Topic/SignTool.exe%20\(Sign%20Tool\).md)   
 [Página Firma, Diseñador de proyectos](../ide/reference/signing-page-project-designer.md)   
 [Cómo: Firmar un ensamblado \(Visual Studio\)](http://msdn.microsoft.com/es-es/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Cómo: Firmar un ensamblado con un nombre seguro](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Ensamblados con nombre seguro](../Topic/Strong-Named%20Assemblies.md)   
 [Firma de nombre seguro para aplicaciones administradas](http://msdn.microsoft.com/es-es/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)