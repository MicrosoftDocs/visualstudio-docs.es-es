---
title: "No se permite un miembro &#39;MustOverride&#39; no conforme a CLS en un &lt;nombreDeClase&gt; conforme a CLS. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40034"
  - "vbc40034"
helpviewer_keywords: 
  - "BC40034"
ms.assetid: 4eb36b3a-1bbe-4e99-9ecb-a12b8729b128
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permite un miembro &#39;MustOverride&#39; no conforme a CLS en un &lt;nombreDeClase&gt; conforme a CLS.
Una clase está marcada como `<CLSCompliant(True)>`, pero contiene una propiedad o un procedimiento `MustOverride` que está marcado como `<CLSCompliant(False)>` o no está marcada.  
  
 Cuando una clase es compatible con la [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), una aplicación que usa dicha clase solo accede a los miembros que también están marcados como `<CLSCompliant(True)>` e ignore aquellos que no lo están. Sin embargo, la aplicación no puede ignorar una propiedad o un procedimiento `MustOverride`, porque debe acceder a esa propiedad o ese procedimiento para reemplazarlo.  
  
 Al aplicar <xref:System.CLSCompliantAttribute> a un elemento de programación, establezca el parámetro `isCompliant` del atributo en `True` o `False` para indicar conformidad o disconformidad. No hay ningún valor predeterminado para este parámetro y debe proporcionar un valor.  
  
 Si no se aplica <xref:System.CLSCompliantAttribute> a un elemento, se considera que no es conforme.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40034  
  
### Para corregir este error  
  
-   Si requiere conformidad con CLS y tener control sobre el código fuente de la clase, marque el miembro como `<CLSCompliant(True)>`.  
  
-   Si requiere conformidad con CLS y no tener control sobre el código fuente de la clase, o si no reúne los requisitos de conformidad, defina a este miembro en otra clase.  
  
-   Si requiere que este miembro siga siendo no conforme, quite la palabra clave `MustOverride` de su definición, quite el <xref:System.CLSCompliantAttribute> de la definición de clase o marque la clase como `<CLSCompliant(False)>`.  
  
## Vea también  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [\<PAVE OVER\> Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3)