---
title: "Enumerador de c&#243;digo de estado de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "constantes con nombre, enumerador SccStatus"
  - "origen control complementos, enumeración del estado de archivo"
  - "Enumerador de SccStatus"
  - "enumerador de código de estado de archivo"
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Enumerador de c&#243;digo de estado de archivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El `SccStatus` enumerador contiene valores constantes con nombre que especifican el estado de un archivo en el sistema de control de código fuente. Esta enumeración se utiliza en el [SccQueryInfo](../extensibility/sccqueryinfo-function.md) y el `POPLISTFUNC` función de devolución de llamada \(consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información\).  
  
## Sintaxis  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## Miembros  
 SCC\_STATUS\_INVALID  
 No se pudo obtener el estado; No confíe en él.  
  
 SCC\_STATUS\_NOTCONTROLLED  
 Archivo no está bajo control de código fuente.  
  
 SCC\_STATUS\_CONTROLLED  
 Archivo está bajo control de código fuente.  
  
 SCC\_STATUS\_CHECKEDOUT  
 Desprotegido por el usuario actual en el disco local.  
  
 SCC\_STATUS\_OUTOTHER  
 Archivo está desprotegido por otro usuario.  
  
 SCC\_STATUS\_OUTEXCLUSIVE  
 Archivo está desprotegido en exclusiva.  
  
 SCC\_STATUS\_OUTMULTIPLE  
 Archivo está desprotegido por más de un usuario.  
  
 SCC\_STATUS\_OUTOFDATE  
 El archivo no es la más reciente.  
  
 SCC\_STATUS\_DELETED  
 Se eliminó el archivo del proyecto.  
  
 SCC\_STATUS\_LOCKED  
 El archivo está bloqueado; No hay más versiones permitidas.  
  
 SCC\_STATUS\_MERGED  
 Se ha combinado pero aún no se han corregido o comprobarán de archivo.  
  
 SCC\_STATUS\_SHARED  
 Archivo está compartido entre proyectos.  
  
 SCC\_STATUS\_PINNED  
 Se comparte el archivo a una versión específica.  
  
 SCC\_STATUS\_MODIFIED  
 Archivo ha sido modificado, roto o infringen.  
  
 SCC\_STATUS\_OUTBYUSER  
 Archivo está desprotegido por el usuario actual.  
  
 SCC\_STATUS\_NOMERGE  
 Archivo nunca se puede mezclar con y no debe guardarse antes de una operación GET.  
  
 SCC\_STATUS\_RESERVED\_1  
 Reservado para uso interno.  
  
 SCC\_STATUS\_RESERVED\_2  
 Reservado para uso interno.  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)