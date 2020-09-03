---
title: Propiedades de una definición de DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8755b1b70051c54157fa87ee0b66dbc9340b5024
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668465"
---
# <a name="properties-of-a-dsl-definition"></a>Propiedades de las definiciones DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las propiedades de DslDefinition definen propiedades *de definición de lenguajes específicos del dominio* , como la numeración de versiones. Las propiedades DslDefinition aparecen en la ventana **propiedades** cuando se hace clic en un área abierta del diagrama en el *Diseñador de lenguaje específico de dominio*.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition tiene las propiedades de la tabla siguiente:

|Propiedad|Descripción|Valor predeterminado|
|--------------|-----------------|-------------|
|Modificador de acceso|Determina si el modificador de acceso de la clase de dominio es público o interno.|public|
|Atributos personalizados|Atributos personalizados definidos para la clase de dominio.<br /><br /> **Nota:** Use el botón Examinar para agregar un atributo.|\<none>|
|Nombre de la empresa|Nombre del nombre de la compañía actual en el registro del sistema.|Nombre de la empresa actual|
|Nombre|Nombre de esta clase de dominio.|Nombre actual|
|Espacio de nombres|Espacio de nombres afiliado a esta clase de dominio.|Espacio de nombres actual|
|GUID del paquete|GUID del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paquete generado para este DSL.|\<none>|
|Espacio de nombres del paquete|Espacio de nombres para el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paquete generado para este DSL.|\<none>|
|Nombre de producto|Nombre del producto que se registrará para el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paquete generado para este DSL.|\<none>|
|Notas|Notas asociadas a esta clase de dominio.|\<none>|
|Descripción|Descripción de esta clase de dominio.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none>|
|Help Keyword|Palabra clave de ayuda asociada a esta clase de dominio.|\<none>|
|Compilar|El número de compilación incremental para esta definición de lenguaje específico de dominio.|0|
|Major Version|El número de compilación principal incremental para esta definición de lenguaje específico de dominio.|1|
|Minor Version|El número de compilación secundaria incremental para esta definición de lenguaje específico de dominio.|0|
|Revisión|El número de compilación de revisión incremental para esta definición de lenguaje específico de dominio.|0|

## <a name="see-also"></a>Consulte también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
