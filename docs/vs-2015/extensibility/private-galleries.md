---
title: Galerías privadas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 820b0e992b79af28ca1b7f65f6a2f6221396da9e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192619"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede compartir los controles, plantillas y herramientas que desarrolla publicándolas en un *Galería privada* en la intranet de su organización, como se indica a continuación:  
  
-   Crear una Atom (RSS) de la fuente en una ubicación central (repositorio) configurada de forma adecuada de la intranet. Para obtener más información, consulte [Cómo: crear una fuente Atom para una galería privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuir un archivo .pkgdef que describe la Galería privada. Se recomienda esta configuración para los administradores que deseen conectarse una galería privada a muchos equipos al mismo tiempo.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Agregar una galería privada a extensiones y actualizaciones en Visual Studio  
 Cuando una galería privada está disponible, puede agregarlo a **extensiones y actualizaciones** en Visual Studio.  
  
 ![Administrador de extensiones de cuadro de diálogo Agregar](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para agregar una galería privada a extensiones y actualizaciones  
  
1.  En la barra de menús, elija **Herramientas**, **Opciones**.  
  
2.  En el **entorno** nodo, seleccione **extensiones y actualizaciones**.  
  
3.  Elija el botón de **Agregar** .  
  
4.  En el **nombre** , escriba un nombre para la Galería privada, por ejemplo, `My Gallery`.  
  
5.  En el **URL** , escriba la dirección URL de la fuente Atom o un sitio de SharePoint que hospeda la Galería privada.  
  
    1.  Si el host es una fuente Atom que se conecta a la Galería privada, la dirección URL sería similar a ésta: http://www.mywebsite/mygallery/atom.xml.  Esta dirección URL puede hacer referencia a un archivo o una ruta de acceso de red.  
  
    2.  Si el host es un sitio de SharePoint, la dirección URL sería similar a ésta: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Administrar galerías privadas  
 Un administrador puede realizar una galería privada disponible en varios equipos al mismo tiempo, modifique el registro del sistema en cada equipo. Para ello, cree un archivo .pkgdef que describe las nuevas claves del registro y sus valores.  El formato de este archivo es como sigue.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Para obtener más información, consulte [Cómo: administrar una privada galería mediante registro opciones](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalación de extensiones de una galería privada  
 Puede buscar e instalar extensiones de Visual Studio desde una galería privada en **extensiones y actualizaciones**. Los pasos siguientes utilizan una galería privada denominada `My Gallery`.  
  
 ![Administrador de extensiones instalando Galería privada](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para buscar e instalar extensiones desde una galería privada  
  
1.  En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2.  En el panel izquierdo, seleccione **extensiones en línea**y, a continuación, seleccione **Mi galería**.  
  
3.  En el panel derecho, seleccione una extensión y, a continuación, elija el **descargar** botón.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Actualización de extensiones de una galería privada  
 En la Galería privada, se publican nuevas versiones de extensiones de Visual Studio, puede actualizar las extensiones que ha instalado. Los pasos siguientes utilizan una galería privada denominada `My Repository`.  
  
 ![Actualización de la Galería privada del Administrador de extensión](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para actualizar una extensión instalada desde una galería privada  
  
1.  En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2.  En el panel izquierdo, seleccione **actualizaciones**y, a continuación, seleccione **Mi repositorio**.  
  
3.  En el panel derecho, seleccione una extensión y, a continuación, elija el **actualización** botón.  
  
## <a name="see-also"></a>Vea también  
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

