---
title: "Alerta de seguridad del servidor de origen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.sourceserver.enablewarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Alerta de seguridad del servidor de origen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si utiliza el servidor de origen, trabaje únicamente con archivos de símbolos procedentes de una ubicación conocida y de confianza.  
  
 Esta advertencia aparece cuando habilita la compatibilidad con el servidor de origen.  Los comandos de servidor de origen se incrustan en archivos de símbolos de depuración \(archivos PDB\).  Asegúrese de que sabe de dónde provienen los archivos PDB.  
  
> [!IMPORTANT]
>  Se deben tener en cuenta las siguientes amenazas potenciales para la seguridad al utilizar el servidor de origen: puede haber comandos arbitrarios incrustados en el archivo PDB de la aplicación, por lo que es necesario asegurarse de poner únicamente los que se desean ejecutar en el archivo srcsrv.ini.  Todo intento de ejecutar un comando no incluido en el archivo srcsvr.ini provocará la aparición de un cuadro de diálogo de confirmación.  Para obtener más información, vea [Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Los parámetros de los comandos no están sujetos a ninguna validación, por lo que se debe tener cuidado con los comandos de confianza.  Por ejemplo, si confiara en cmd.exe, un usuario malintencionado podría especificar parámetros que harían que el comando fuera peligroso.  
  
## Vea también  
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)