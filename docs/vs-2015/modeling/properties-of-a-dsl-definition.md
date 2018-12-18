---
title: Propiedades de una definición de DSL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 50b4325d2329bbaf402dcf2f059c51b5a796bdcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197371"
---
# <a name="properties-of-a-dsl-definition"></a>Propiedades de las definiciones DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definen propiedades DslDefinition *lenguajes específicos de dominio* propiedades como la numeración de versiones de la definición. Las propiedades DslDefinition aparecen en la **propiedades** ventana al hacer clic en un área abierta del diagrama en el *Diseñador de lenguaje específico de dominio*.  
  
 Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition tiene las propiedades en la tabla siguiente:  
  
|Property|Descripción|Default|  
|--------------|-----------------|-------------|  
|Modificador de acceso|Determina si el modificador de acceso de la clase de dominio es público o interno.|public|  
|Atributos personalizados|Personalizado definido por los atributos de la clase de dominio.<br /><br /> **Tenga en cuenta** Use el botón Examinar para agregar un atributo.|\<Ninguno >|  
|Nombre de la compañía|El nombre de la empresa actual en el registro del sistema.|Nombre de la empresa actual|  
|nombre|El nombre de esta clase de dominio.|Nombre actual|  
|Espacio de nombres|El espacio de nombres asociado a esta clase de dominio.|Espacio de nombres actual|  
|Guid del paquete|El guid para el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paquete generado para este DSL.|\<Ninguno >|  
|Paquete Namespace|El espacio de nombres para el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paquete generado para este DSL.|\<Ninguno >|  
|Nombre de producto|El nombre del producto que se registrará para el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paquete generado para este DSL.|\<Ninguno >|  
|Notas|Notas asociadas a esta clase de dominio.|\<Ninguno >|  
|Descripción|Descripción de esta clase de dominio.|\<Ninguno >|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<Ninguno >|  
|Help Keyword|La palabra clave de ayuda asociada a esta clase de dominio.|\<Ninguno >|  
|Compilar|El número de compilación incremental para esta definición de lenguaje específico de dominio.|0|  
|Versión principal|El número de compilación principal incrementales para esta definición de lenguaje específico de dominio.|1|  
|Versión secundaria|El número de compilación secundaria incrementales para esta definición de lenguaje específico de dominio.|0|  
|Revisión|La revisión incremental número de compilación para esta definición de lenguaje específico de dominio.|0|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



