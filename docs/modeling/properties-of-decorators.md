---
title: "Propiedades de los decoradores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, decoradores"
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 23
caps.handback.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propiedades de los decoradores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los elementos decorator son iconos, texto, o expandir o los botones de contenido adicional de recepción que pueden aparecer en formas o conectores del diagrama.  Las tablas siguientes se muestran las propiedades de las tres clases de decorador.  Algunas propiedades solo aparecen en decoradores de la forma o sólo en decoradores de conectores.  
  
 Para obtener más información, vea [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).  Para obtener más información sobre cómo utilizar estas propiedades, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## Expandir o el decorador expandcollapse  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|DisplayName|El nombre de decorador que se mostrará en el diseñador generado.|Expanda el elemento decorator expandcollapse|  
|Name|El nombre de decorador.|ExpandCollapseDecorator|  
|Notas|Notas informales que son asociado a este elemento decorator.|\<none\>|  
|HorizontalOffset|El desplazamiento horizontal, en relación con la posición predeterminada de decorador, en pulgadas.  \(En formas sólo.\)|0|  
|VerticalOffset|El desplazamiento vertical, en relación con la posición predeterminada de decorador, en pulgadas.  \(En formas sólo.\)|0|  
|OffsetFromLine|El desplazamiento de decorador de línea, relativa a su posición predeterminada, en pulgadas.  \(En los conectores sólo.\)|0|  
|OffsetFromShape|El desplazamiento de decorador de la forma, en relación con su posición predeterminada, en pulgadas.  \(En los conectores sólo.\)|0|  
|Posición|La posición predeterminada de decorador.|SourceTop|  
  
## Decorador de icono  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|DefaultIcon|La ruta de acceso del icono o del archivo de imagen que se mostrarán.|\<none\>|  
|DisplayName|El nombre de decorador se muestre en el diseñador generado.|Decorador de icono|  
|Name|El nombre de decorador.|IconDecorator|  
|Notas|Notas informales que son asociado con el elemento decorator.|\<none\>|  
|HorizontalOffset|El desplazamiento horizontal, en relación con la posición predeterminada de decorador, en pulgadas.  \(En formas sólo.\)|0|  
|VerticalOffset|El desplazamiento vertical, en relación con la posición predeterminada de decorador, en pulgadas.  \(En formas sólo.\)|0|  
|OffsetFromLine|El desplazamiento de decorador de línea, relativa a su posición predeterminada, en pulgadas.  \(En los conectores sólo.\)|0|  
|OffsetFromShape|El desplazamiento de decorador de la forma, en relación con su posición predeterminada, en pulgadas.  \(En los conectores sólo.\)|0|  
|Posición|La posición predeterminada de decorador.|SourceTop|  
  
## TextDecorator  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|DefaultText|El texto predeterminado que se va a mostrar.|Etiqueta|  
|DisplayName|El nombre de decorador se muestre en el diseñador generado.|Etiqueta|  
|FontSize|El tamaño de fuente del texto que se muestra en el elemento decorator.|8|  
|FontStyle|El estilo de fuente del texto que se muestra en el elemento decorator.|Estándar|  
|Name|El nombre de decorador.|Etiqueta|  
|Notas|Notas informales que son asociado con el elemento decorator.|\<none\>|  
|HorizontalOffset|El desplazamiento horizontal, en relación con la posición predeterminada de decorador, en pulgadas.  \(En formas sólo.\)|0|  
|VerticalOffset|El desplazamiento vertical, en relación con la posición predeterminada de decorador, en pulgadas.  \(En formas sólo.\)|0|  
|OffsetFromLine|El desplazamiento de decorador de línea, relativa a su posición predeterminada, en pulgadas.  \(En los conectores sólo.\)|0|  
|OffsetFromShape|El desplazamiento de decorador de la forma, en relación con su posición predeterminada, en pulgadas.  \(En los conectores sólo.\)|0|  
|Posición|La posición predeterminada de decorador.|TargetBottom|  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)