---
title: "Propiedades de una definición DSL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 7a8fc0474f624785a47a4ba9f970b5a1ca54dd9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-a-dsl-definition"></a>Propiedades de las definiciones DSL
Definen propiedades DslDefinition *lenguaje específico de dominio* propiedades como la numeración de la versión de la definición. Las propiedades de DslDefinition aparecen en la **propiedades** ventana al hacer clic en un área abierta del diagrama en el *Diseñador de lenguaje específico de dominio*.  
  
 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition tiene las propiedades en la tabla siguiente:  
  
|Propiedad|Descripción|Default|  
|--------------|-----------------|-------------|  
|Modificador de acceso|Determina si el modificador de acceso para la clase de dominio es pública o interna.|public|  
|Atributos personalizados|Personalizado definido atributos para la clase de dominio.<br /><br /> **Tenga en cuenta** utilice el botón Examinar para agregar un atributo.|\<Ninguno >|  
|Nombre de la compañía|El nombre de la empresa actual en el registro del sistema.|Nombre de la compañía actual|  
|Name|El nombre de esta clase de dominio.|Nombre actual|  
|Espacio de nombres|El espacio de nombres asociado a esta clase de dominio.|Espacio de nombres actual|  
|Guid del paquete|El guid para el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paquete generado para este DSL.|\<Ninguno >|  
|Paquete Namespace|El espacio de nombres para el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paquete generado para este DSL.|\<Ninguno >|  
|Nombre de producto|El nombre del producto que se registrará para el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paquete generado para este DSL.|\<Ninguno >|  
|Notas|Notas asociadas a esta clase de dominio.|\<Ninguno >|  
|Descripción|Descripción para esta clase de dominio.|\<Ninguno >|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<Ninguno >|  
|Help Keyword|La palabra clave de ayuda asociada a esta clase de dominio.|\<Ninguno >|  
|Compilar|El número de compilación incremental para esta definición de lenguaje específico de dominio.|0|  
|Versión principal|El número de compilación principal incrementales para esta definición de lenguaje específico de dominio.|1|  
|Versión secundaria|El número de compilación secundaria incrementales para esta definición de lenguaje específico de dominio.|0|  
|Revisión|La revisión incremental número de compilación para esta definición de lenguaje específico de dominio.|0|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)