---
title: "Editar consulta guardar (VSPackage del Control de c&#243;digo fuente) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eventos QEQS"
  - "Editar consulta guardar eventos de consulta"
  - "paquetes de control de código fuente, consulta Editar consulta guardar eventos"
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Editar consulta guardar (VSPackage del Control de c&#243;digo fuente)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

los editores de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden los eventos Save de la consulta de \(QEQS\) la consulta de difusión.  el código auxiliar de control de código fuente de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementa el servicio de QEQS, de modo que el remitente de eventos de QEQS.  Estos eventos se delegan actualmente al control de código fuente activo VSPackage.  el control de código fuente activo VSPackage implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y sus métodos.  Los métodos de la interfaz de `IVsQueryEditQuerySave2` se denominan normalmente inmediatamente antes que un documento se edita por primera vez e inmediatamente antes de que se guarda un documento.  
  
## eventos de QueryEditQuerySave  
 El control de código fuente VSPackage debe controlar los eventos de QEQS implementando la interfaz de `IVsQueryEditQuerySave2` y los métodos necesarios.  A continuación se muestra una breve descripción de los dos métodos que el Paquete debe implementar en un mínimo.  La implementación real debe coincidir con la lógica del modelo de control de código fuente.  
  
### método de QueryEditFiles  
 Se llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a cualquier proyecto o editor desea modificar un archivo.  Idealmente, se llama a este método *antes* que se modifica el archivo y cuando se guarda un archivo.  Cuando se invoca, el método de `IVsQueryEditQuerySave2::QueryEditFiles` comprueba si los archivos especificados están bajo control de código fuente, si es necesario desprotegidos, y si pueden volver.  Si las circunstancias impiden que los archivos son modificables, el método de `IVsQueryEditQuerySave2::QueryEditFiles` indica al programa de llamada que cancelar la edición.  También es posible que el llamador especifique un modo de invocación.  En el modo “silencioso”, este método toma medidas solo si no realiza ninguna interfaz de usuario que aparezca.  si la interfaz de usuario es inevitable, un indicador se debe devolver para indicar el problema.  
  
 El método se comporta de un modo transaccional; es decir, si la edición se cancela en un solo archivo, la edición se cancela para todos los archivos.  A la inversa, si se permite la edición, se permite que todos los archivos.  Si este método permite la edición una vez para un conjunto de archivos determinado, debe permitir siempre la edición de las llamadas subsiguientes del mismo conjunto de archivos.  El bucle de la permitir\-edición continúa hasta que los archivos están cerrados, guardar, y recargados; hasta el cambio de los atributos \(propiedades\); o hasta el paquete de control de código fuente se cambia.  Casos a ver en implementar varios archivos de inclusión del método de `IVsQueryEditQuerySave2::QueryEditFiles` , archivos especiales, la eliminación del usuario, y las ediciones de memoria.  
  
### método de QuerySaveFiles  
 Se llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> a cualquier proyecto o editor necesita guardar un conjunto de archivos.  Cuando se invocan, las comprobaciones del método de `IVsQueryEditQuerySave2::QuerySaveFiles` si los archivos especificados son de solo lectura y si están bajo control de código fuente.  Si los archivos deben ser desprotegidos, la llamada se delega en el paquete de control de código fuente.  Si las circunstancias impiden que los archivos se guardarán, el método de `IVsQueryEditQuerySave2::QuerySaveFiles` debe indicar el editor que cancelar guardado.  Como con el método de `IVsQueryEditQuerySave2::QueryEditFiles` , es posible que el llamador especifique un modo de invocación.  En el modo “silencioso”, este método toma medidas solo si no realiza ninguna interfaz de usuario que aparezca.  si la interfaz de usuario es inevitable, un indicador se debe devolver para indicar el problema.  
  
 Este método debe comportarse de manera transaccional; es decir, si guardado se cancela en un único archivo, guardado se cancela para todos los archivos.  A la inversa, si se permite guardado, debe ser permitida para todos los archivos.  Como con el método de `IVsQueryEditQuerySave2::QueryEditFiles` , los casos a ver en implementar varios archivos de inclusión del método de `IVsQueryEditQuerySave2::QuerySaveFiles` , archivos especiales, la eliminación del usuario, y las ediciones de memoria.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>