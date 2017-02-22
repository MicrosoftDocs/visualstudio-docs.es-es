---
title: "Opciones de IntelliSense espec&#237;ficas de Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [Visual Basic]"
  - "IntelliSense [Visual Studio], Visual Basic"
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones de IntelliSense espec&#237;ficas de Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El editor de código fuente de Visual Basic ofrece las siguientes características de IntelliSense:  
  
-   Sugerencias de sintaxis  
  
     Las sugerencias de sintaxis muestran la sintaxis de la instrucción que está escribiendo.  Esto resulta útil para instrucciones como [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).  
  
## Finalización automática  
  
-   Finalización de varias palabras clave  
  
     Por ejemplo, si escribe `goto` y un espacio, IntelliSense muestra una lista de las etiquetas definidas en un menú desplegable.  Otras palabras clave admitidas son `Exit`, `Implements`, `Option` y `Declare`.  
  
-   Finalización en `Enum` y `Boolean`  
  
     Cuando una instrucción hace referencia a un miembro de una enumeración, IntelliSense mostrará la lista de los miembros de `Enum`.  Cuando una instrucción hace referencia a un tipo de datos `Boolean`, IntelliSense muestra un menú desplegable de verdadero o falso.  
  
 Para desactivar la finalización de forma predeterminada, desactive **Lista de miembros automática** en la página de propiedades **General** de la carpeta **Visual Basic**.  
  
 Puede invocar manualmente la finalización invocando a Lista de Miembros, Palabra completa o presionando ALT\+FLECHA DERECHA.  Para obtener más información, vea [Utilizar IntelliSense](../ide/using-intellisense.md).  
  
## IntelliSense en zona  
 IntelliSense en zona ayuda a los desarrolladores de Visual Basic que necesitan implementar aplicaciones a través de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y están forzados a configuraciones de confianza parcial.  Esta característica:  
  
-   Permite elegir los permisos con los que se ejecutará la aplicación.  
  
-   Muestra las API de la zona elegida como disponibles en la Lista de miembros y las API que requieren permisos adicionales, como no disponibles.  
  
 Para obtener más información, vea [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## Vea también  
 [Utilizar IntelliSense](../ide/using-intellisense.md)