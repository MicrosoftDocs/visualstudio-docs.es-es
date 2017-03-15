---
title: "Determinar si se debe implementar en un VSPackage del Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paquetes de control de origen, acerca de los paquetes de control de código fuente"
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Determinar si se debe implementar en un VSPackage del Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta sección prepara las opciones de los complementos y control de código fuente VSPackages de control de código fuente de las soluciones de control de código fuente que extienden y proporciona instrucciones generales sobre cómo elegir una ruta de acceso adecuada de integración.  
  
## Pequeña solución de control de código fuente con recursos limitados  
 Si ha limitado recursos y no se puede cargar con la sobrecarga de escribir un paquete de control de código fuente, puede crear complementos API\-basados complemento de control de código fuente.  Esto le permitirá trabajar en paralelo con los paquetes de control de código fuente, y cambiar entre los complementos de control de código fuente y paquetes a petición.  Para obtener más información, vea [Selección y registro](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## Solución de Control grande de origen con un conjunto de características enriquecidas  
 Si desea implementar una solución de control de código fuente que proporciona un modelo de control de código fuente enriquecido que adecuadamente no se captura mediante el complemento de control de código fuente API, puede considerar un paquete de control de código fuente como la ruta de integración.  Esto se aplica especialmente si reemplazaría suficiente el paquete de adaptador de control de código fuente \(que se comunica con los complementos de control de código fuente y proporciona una interfaz de usuario básica de control de código fuente\) con dispone de modo que puede controlar los eventos de control de código fuente de una manera personalizada.  Si tiene una interfaz de usuario satisfactoria de control de código fuente y la desea ya para conservar esa experiencia en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la opción de paquete de control de código fuente le permite hacer exactamente eso.  El paquete de control de código fuente no es genérico y está diseñado para usarlos con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE.  
  
 Si desea implementar una solución de control de código fuente que proporciona flexibilidad y un control más completo sobre la lógica y la interfaz de usuario de control de código fuente, puede optar por la ruta de la integración del paquete de control de código fuente.  Puede realizar lo siguiente:  
  
1.  Registre poseen el control de código fuente VSPackage \(vea [Selección y registro](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)\).  
  
2.  Reemplace la interfaz de usuario predeterminada del control de código fuente con la interfaz de usuario personalizada \(vea [Interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)\).  
  
3.  Especifique los glifos que se van a utilizar y administrar los eventos de glifo del explorador de soluciones \(vea [Control de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)\).  
  
4.  Edición de consulta ID y eventos Save de la consulta \(vea [Guardar la consulta Editar consulta](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)\).  
  
## Vea también  
 [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)