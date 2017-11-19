---
title: "Declaración de soporte para Visual Basic 6.0 | Documentos de Microsoft"
ms.date: 08/28/2017
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs: VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.openlocfilehash: bdfe33cac19d488bc7763f3c61c518093d8afffa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Declaración de soporte para Visual Basic 6.0 en Windows


## <a name="executive-summary"></a>Resumen ejecutivo

El equipo de Visual Basic se compromete a la compatibilidad de "Simplemente funciona" para aplicaciones de Visual Basic 6.0 en los siguientes sistemas operativos de Windows compatibles: 

- Windows 10 
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 incluido R2
- Windows Server 2008 R2 de incluido

Los objetivos del equipo de Visual Basic es que las aplicaciones de Visual Basic 6.0 seguirán ejecutando en versiones compatibles de Windows. Como se detalla en este documento, el tiempo de ejecución de Visual Basic 6.0 core será compatible para la duración completa de las versiones compatibles de Windows, que es de cinco años de soporte estándar, seguido de cinco años de soporte extendido (http://support.microsoft.com/gp/lifepolicy). La barra de soporte técnico se limitará a regresiones graves y problemas de seguridad críticos para las aplicaciones existentes.

## <a name="technical-summary"></a>Resumen técnico

Visual Basic 6.0 se compone de estos productos claves:
- Visual Basic 6.0 IDE (entorno de desarrollo integrado).
- En tiempo de ejecución de Visual Basic 6.0: las bibliotecas base y el motor de ejecución utilizada para ejecutar aplicaciones de VB 6.0.
- Archivos de extendido en tiempo de ejecución de Visual Basic 6.0: seleccionar archivos OCX de control de ActiveX, las bibliotecas y herramientas de envío con el medio IDE y como una versión en línea.

## <a name="the-visual-basic-60-ide"></a>El IDE de 6.0 Visual Basic

El IDE de Visual Basic 6.0 ya no se admite a partir del 8 de abril de 2008. Además, los equipos de Windows y Visual Basic han probado IDE de Visual Basic 6.0 en Windows Vista, Windows 7, Windows Server 2008, Windows 8 y Windows 8.1 para comprender y mitigar (si procede) problemas de compatibilidad en las versiones de 32 bits de Windows (consulte el [Windows de 64 bits](#62-bit-windows) sección para obtener más información acerca de los sistemas de 64 bits). Este anuncio no cambia la directiva de soporte técnico para el IDE.

## <a name="the-visual-basic-60-runtime"></a>El tiempo de ejecución de Visual Basic 6.0

El tiempo de ejecución de Visual Basic 6.0 se define como los archivos binarios compilados incluidos originalmente en la lista de redistribución de Visual Basic 6.0. Estos archivos se han marcado como distribuible en la licencia de Visual Basic 6.0 original. Ejemplos de estos archivos, la biblioteca en tiempo de ejecución de Visual Basic 6.0 (`msvbvm60.dll`), controles (es decir, `msflxgrd.ocx`) junto con el tiempo de ejecución de los archivos auxiliares de otras áreas funcionales principales (es decir, MDAC).

El tiempo de ejecución se divide en tres grupos:

- Admite archivos de tiempo de ejecución: envío en el sistema operativo

   Los archivos de en tiempo de ejecución de clave de Visual Basic 6.0, utilizados en la mayoría de los escenarios de aplicaciones, se incluyen en y compatible con la duración de las versiones compatibles de Windows. Esta duración es de cinco años de soporte técnico y cinco años de soporte extendido desde el momento en que se suministra una versión concreta de Windows. Estos archivos se ha probado la compatibilidad como parte de nuestras pruebas de aplicaciones de Visual Basic 6.0 que se ejecutan en versiones de Windows compatibles. 

   > [!NOTE]
   > Todas las versiones compatibles de Windows contienen una lista de archivos prácticamente idéntica, y los requisitos de paquete redistribuible para aplicaciones que contienen estos archivos deben ser casi idénticos. Una diferencia clave es que `TriEdit.dll` se ha quitado de Windows Vista y versiones posteriores.

- Admite archivos de tiempo de ejecución:-archivos para distribuir con la aplicación extendidos

   Esta lista extendida está formada por controles de tecla, bibliotecas y herramientas que se instalan desde el medio IDE o desde Microsoft.com en el equipo del desarrollador. Normalmente, el IDE VB6 instala estos controles en el equipo del desarrollador de forma predeterminada. El desarrollador debe seguir redistribuir estos archivos con la aplicación. La versión admitida de los archivos está disponible en línea en Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkID=142927).

- Archivos en tiempo de ejecución no compatible

   Algunos archivos cualquiera ha caído estándar admiten o nunca se incluyeron como parte de la redistribución en tiempo de ejecución (por ejemplo, se incluyen en el `\Tools` carpeta en el disco IDE para admitir aplicaciones heredadas de VB4/VB5, o estaban controles de terceros). Estos archivos no se admiten en Windows; en su lugar, están sujetos a cualquier contrato de soporte técnico se aplica a los medios que se enviaron con. Esto no implica ninguna garantía alrededor de soporte técnico y servicio. En algunos casos, se admiten las versiones posteriores de estas bibliotecas. A continuación, se proporcionan detalles sobre compatibilidad con versiones anteriores o la migración a versiones compatibles.

Para conocer detalles concretos sobre los archivos incluidos en cada grupo de soporte técnico, consulte el [definición en tiempo de ejecución](#runtime-definition) sección más adelante.

## <a name="the-visual-basic-60-support-lifetime"></a>El tiempo de vida de soporte técnico de Visual Basic 6.0

Admitir ni un envío de archivos binarios en tiempo de ejecución de Visual Basic 6.0 en versiones compatibles de Windows no cambia la directiva de soporte técnico para el IDE de Visual Basic 6.0 o Visual Studio 6.0 IDE como un todo. Los productos salen de soporte extendido de 8 de abril de 2008.

Obtener más información sobre el ciclo de vida de soporte técnico de productos de Microsoft se puede encontrar en http://support.microsoft.com/gp/lifepolicy. Como parte de este ciclo de vida de soporte técnico, Microsoft seguirá admitir el tiempo de ejecución de Visual Basic 6.0 en versiones compatibles de Windows para la duración de soporte técnico de estos sistemas operativos. Por ejemplo, esto significa que el tiempo de ejecución de Visual Basic 6.0 se admitirán en Windows Server 2003 hasta junio de 2008 para el soporte técnico y junio de 2013 de soporte extendido.
Para obtener más detalles sobre el ciclo de vida de soporte técnico o para obtener información sobre opciones de soporte adicionales, visite nuestra página de soporte técnico en http://www.microsoft.com/support.

## <a name="64-bit-windows"></a>Windows de 64 bits

Archivos de tiempo de ejecución de Visual Basic 6.0 son de 32 bits. Estos archivos se incluyen en 64 bits sistemas operativos Windows al que hace referencia en la tabla siguiente. en el entorno de emulación de WOW solo se admiten componentes y aplicaciones de VB6 de 32 bits. También se deben hospedar los componentes de 32 bits en procesos de aplicación de 32 bits.

El IDE de Visual Basic 6.0 nunca se han proporcionado en una versión de 64 bits nativa, ni el IDE de 32 bits compatible en Windows de 64 bits. Desarrollo de VB6 en Windows de 64 bits o en cualquier arquitectura nativo que no sea de 32 bits no es y no se admite.

## <a name="windows-7"></a>Windows 7

Desde la versión inicial de esta afirmación de compatibilidad, el sistema operativo Windows 7 se ha liberado. Este documento se actualizó para aclarar el soporte técnico de Microsoft para VB6 en Windows 7.

El runtime de VB6 se incluirá y será compatible con Windows 7 durante la vigencia del sistema operativo. Archivos de tiempo de ejecución de Visual Basic 6.0 siguen estando sólo de 32 bits, y todos los componentes se deben hospedar en procesos de aplicación de 32 bits.

## <a name="windows-81"></a>Windows 8.1

Desde la versión inicial de esta afirmación de compatibilidad, el sistema operativo de Windows 8.1 se ha liberado. Este documento se actualizó para aclarar el soporte técnico de Microsoft para VB6 en Windows 8.1.

El runtime de VB6 se incluirá y será compatible con Windows 8.1 durante la vigencia del sistema operativo. Archivos de tiempo de ejecución de Visual Basic 6.0 siguen estando sólo de 32 bits, y todos los componentes se deben hospedar en procesos de aplicación de 32 bits. Los programadores pueden considerar el caso de soporte técnico para Windows 8.1 como el mismo como para Windows 7.

## <a name="windows-10"></a>Windows 10 

Desde la versión inicial de esta afirmación de compatibilidad, el sistema operativo Windows 10 se ha liberado. Este documento se actualizó para aclarar el soporte técnico de Microsoft para VB6 en Windows 10.

El runtime de VB6 se incluirá y será compatible con Windows 10 durante la vigencia del sistema operativo. Archivos de tiempo de ejecución de Visual Basic 6.0 siguen estando sólo de 32 bits, y todos los componentes se deben hospedar en procesos de aplicación de 32 bits. Los programadores pueden considerar el caso de soporte técnico para Windows 10 como el mismo como para Windows 8.1.

## <a name="windows-server-2008"></a>Windows Server 2008

Desde la versión inicial de esta afirmación de compatibilidad, el sistema operativo Windows Server 2008 se ha liberado. Este documento se actualizó para aclarar el soporte técnico de Microsoft para VB6 en Windows Server 2008.

El runtime de VB6 se incluirá y se admitirán en Windows Server 2008 durante la vigencia del sistema operativo. Archivos de tiempo de ejecución de Visual Basic 6.0 siguen estando sólo de 32 bits, y todos los componentes se deben hospedar en procesos de aplicación de 32 bits.

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

Desde la versión inicial de esta declaración de soporte técnico, se ha liberado el sistema operativo Windows Server 2008 R2. Este documento se actualizó para aclarar el soporte técnico de Microsoft para VB6 en Windows Server 2008 R2.

El runtime de VB6 se incluirá y será compatible con Windows Server 2008 R2 durante la vigencia del sistema operativo. Archivos de tiempo de ejecución de Visual Basic 6.0 siguen estando sólo de 32 bits, y todos los componentes se deben hospedar en procesos de aplicación de 32 bits. Los programadores pueden considerar el caso de soporte técnico para Windows Server 2008 R2 como el mismo como para Windows Server 2008.

## <a name="windows-server-2012"></a>Windows Server 2012

Desde la versión inicial de esta afirmación de compatibilidad, el sistema operativo Windows Server 2012 se ha liberado. Este documento se actualizó para aclarar el soporte técnico de Microsoft para VB6 en Windows Server 2012.

El runtime de VB6 se incluirá y será compatible con Windows Server 2012 durante la vigencia del sistema operativo. Archivos de tiempo de ejecución de Visual Basic 6.0 siguen estando sólo de 32 bits, y todos los componentes se deben hospedar en procesos de aplicación de 32 bits. Los programadores pueden considerar el caso de soporte técnico para Windows Server 2012 como el mismo como para Windows Server 2008 R2.

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

Desde la versión inicial de esta afirmación de compatibilidad, el sistema operativo Windows Server 2012 R2 se ha liberado. Este documento se actualizó para aclarar el soporte técnico de Microsoft para VB6 en Windows Server 2012 R2.

El runtime de VB6 se incluirá y será compatible con Windows Server 2012 R2 durante la vigencia del sistema operativo. Archivos de tiempo de ejecución de Visual Basic 6.0 siguen estando sólo de 32 bits, y todos los componentes se deben hospedar en procesos de aplicación de 32 bits. Los programadores pueden considerar el caso de soporte técnico para Windows Server 2012 R2 como el mismo como para Windows Server 2012.

## <a name="windows-server-2016"></a>Windows Server 2016

Desde la versión inicial de esta afirmación de compatibilidad, el sistema operativo Windows Server 2016 se ha liberado. Este documento se actualizó para aclarar el soporte técnico de Microsoft para VB6 en Windows Server 2016.

El runtime de VB6 se incluirá y se admitirán en Windows Server 2016 durante la vigencia del sistema operativo. Archivos de tiempo de ejecución de Visual Basic 6.0 siguen estando sólo de 32 bits, y todos los componentes se deben hospedar en procesos de aplicación de 32 bits. Los programadores pueden considerar el caso de soporte técnico para Windows Server 2016 como el mismo como para Windows Server 2012 R2.

## <a name="supported-windows-operating-system-versions"></a>Versiones de sistemas operativos Windows admitidas

Esta sección proporciona información adicional acerca de los sistemas operativos que ofrecen un nivel de compatibilidad para VB6. 

|Sistema operativo Windows|VB6 Tiempo de ejecución admitida</br>¿Archivos de envío de Windows tienen compatibilidad?|VB6 Admite Rutime</br>Archivos extendidos</br>¿para distribuir con la aplicación dispone de soporte técnico?| ¿IDE de VB6 tiene soporte técnico?|
|---|---|---|---|
|Todas las ediciones de 32 bits de Windows 10|Sí *|Sí *|No|
|Windows 10, todas las ediciones de 64 bits (WOW solo)|Sí * </br> aplicaciones de 32 bits que se ejecutan en WOW solo|Sí* </br> aplicaciones de 32 bits que se ejecutan en WOW solo|No|
|Windows 8.1, todas las ediciones de 32 bits|Sí *|Sí *|No|
| Windows 8.1, todas las ediciones de 64 bits (WOW solo)|Sí * </br> aplicaciones de 32 bits que se ejecutan en WOW solo|Sí* </br> aplicaciones de 32 bits que se ejecutan en WOW solo|No|
|Windows 7, todas las ediciones de 32 bits|Sí *|Sí *|No|
|Windows 7, todas las ediciones de 64 bits (WOW solo)|Sí * </br> aplicaciones de 32 bits que se ejecutan en WOW solo|Sí * </br> aplicaciones de 32 bits que se ejecutan en WOW solo|No|
|Windows Server 2016, todas las ediciones de 64 bits (WOW solo)|Sí* </br> aplicaciones de 32 bits que se ejecutan en WOW solo|Sí* </br> aplicaciones de 32 bits que se ejecutan en WOW solo|No|
|Windows Server 2012 R2, todas las ediciones de 64 bits (WOW solo)<br>Windows Server 2012, todas las ediciones de 64 bits (WOW solo)|Sí* </br> aplicaciones de 32 bits que se ejecutan en WOW solo|Sí* </br> aplicaciones de 32 bits que se ejecutan en WOW solo|No|
|Windows Server 2008 R2, x64 todas las ediciones (solo WOW)</br>Windows Server 2008, x64 todas las ediciones (solo WOW)|Sí * </br> aplicaciones de 32 bits que se ejecutan en WOW solo|Sí * </br> aplicaciones de 32 bits que se ejecutan en WOW solo|No|
|Windows Server 2008, todas las ediciones de 32 bits|Sí *|Sí *|No|


> [!NOTE]
> &#42;  Compatibilidad de runtime de VB6 está limitado por el ciclo de vida de soporte técnico de Windows.  Por ejemplo, si el sistema operativo de destino está en soporte extendido, VB6 no puede tener un mayor nivel de soporte técnico de soporte técnico ampliado.  El [hoja informativa de ciclo de vida de soporte de Windows](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet) contiene información de ciclo de vida adicionales acerca de las versiones de Windows anteriores y actuales.

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Uso de tiempo de ejecución de Visual Basic 6.0 dentro de VBA y Office

Visual Basic para aplicaciones o VBA, es una tecnología distinta usada para la automatización de la aplicación macros dentro de otras aplicaciones, normalmente dentro de aplicaciones de Microsoft Office. VBA se distribuye como parte de Office y, por tanto, la compatibilidad con VBA se rige por la directiva de soporte técnico de Office. Sin embargo, hay situaciones donde es usar VBA para llamar a o para hospedar los controles y los archivos binarios en tiempo de ejecución de Visual Basic 6.0. En estos casos, Visual Basic 6.0 admite archivos de tiempo de ejecución en el sistema operativo y la lista de archivos extendidas también se admiten cuando se utiliza dentro de un entorno compatible con VBA.

Para que escenarios en tiempo de ejecución de VB6 que deben admitir dentro de VBA, deben cumplirse todos los elementos siguientes:

- Todavía se admite la versión del SO host en tiempo de ejecución VB.
- Todavía se admite la versión de host de Office para VBA.
- Todavía se admiten los archivos en tiempo de ejecución en cuestión.

## <a name="visual-basic-script-vbscript"></a>Script de Visual Basic (VBScript)

VBScript está relacionado con Visual Basic 6.0 y esta afirmación de compatibilidad. Sin embargo, VBScript actualmente se envía como parte de Windows 7, Windows 8.1, Windows 10, Windows Server 2008 R2, Windows Server 2012 incluido R2 y Windows Server 2016 de incluido y se rige por el ciclo de vida de soporte técnico del sistema operativo.

## <a name="third-party-components"></a>Componentes de terceros

Microsoft no ha podido proporcionar soporte técnico para los componentes de terceros, como los controles ActiveX/OCX. Se recomienda ponerse en contacto con el proveedor de control original para obtener más información acerca de los componentes de compatibilidad con los clientes.

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Informar de problemas con aplicaciones de VB 6.0 que se ejecutan en Windows

Los desarrolladores que pretende utilizar Visual Basic 6.0 con uno de los sistemas operativos enumerados de Windows deben instalar un sistema operativo y empezar a probar la compatibilidad de aplicaciones con pruebas de aceptación de aplicación original.

Si encuentra un problema con la aplicación de Visual Basic 6.0 en uno de los sistemas operativos enumerados de Windows, siga los canales de soporte normales para notificar el problema.

## <a name="supported-and-shipping-in-windows"></a>Compatible y envío en Windows

| | | | |
|---|---|---|---|
|ATL.dll|         msadcor.dll|     Sqlsrv32|   OLE2.dll|
|Asycfilt.dll|    Msadcs.dll|      Msvbvm60.dll|   Ole32.dll|
|Comcat.dll|      MSADDS.dll|      Msvcirt.dll|    Oleaut32.dll|
|compobj.dll|     msaddsr.dll|     Msvcrt.dll|     Oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    MSVCRT40.dll|   Oledb32.dll|
|DCOMCNFG.exe|    msado15.dll|     Mtxdm.dll|      Oledb32r.dll|
|Dllhost.exe|     Msador15.dll|    Mtxoci.dll|     OLEDLG.dll|
|Ds16gt.dll|      msadrh15.dll|    Odbc16gt.dll|   OLEPRO32.dll|
|ds32gt.dll|      Mscpxl32.dll|    Odbc32.dll|     Olethk32.dll|
|Expsrv.dll|      msdadc.dll|      Odbc32gt.dll|   regsvr32.exe|
|hh.exe|          MSDAENUM.dll|    Odbcad32.exe|   Rpcns4.dll|
|Hhctrl.ocx|      msdaer.dll|      Odbccp32.cpl|   Rpcrt4.dll|
|Imagehlp.dll|    MSDAORA.dll|     Odbccp32.dll|   Scrrun.dll|
|iprop.dll|       msdaosp.dll|     Odbccr32.dll|   Secur32.dll|
|Itircl.dll|      Msdaprst.dll|    Odbccu32.dll|   simpdata.tlb|
|ITSS.dll|        MSDAPS.dll|      Odbcint.dll|    SQLOLEDB.dll|
|Mfc40.dll|       MSDASC.dll|      Odbcji32.dll|   Sqlsrv32.dll|
|Mfc42.dll|       MSDASQL.dll|     Odbcjt32.dll|   Stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    Odbctrac.dll|   stdole32.tlb|
|Msadce.dll|      msdatsrc.tlb|    Oddbse32.dll|   Storage.dll|
|msadcer.dll|     msdatt.dll|      Odexl32.dll|    Vbajet32.dll|
|msadcf.dll|      MSDFMAP.dll|     Odfox32.dll|    Vfpodbc.dll|
|msadcfr.dll|     MSDFMAP.ini|     Odpdx32.dll|                |
|Msadco.dll|      Msjtes40.dll|    Odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>Archivos de tiempo de ejecución admitidas para distribuir con la aplicación

| | | | |
|---|---|---|---|
|Comct232.ocx |msbind.dll   |msdbrptr.dll  |MSstdfmt.dll| 
|COMCT332. |mscdrun.dll  |archivo Msflxgrd.ocx  |msstkprp.dll| 
|Comctl32.ocx |Mschrt20.ocx |mshflxgd.ocx  |mswcrun.dll|  
|Comdlg32.ocx |Mscomct2.ocx |mshtmpgr.dll  |Mswinsck.ocx| 
|dbadapt.dll  |Mscomctl.ocx |MSINET.ocx    |picclp32.ocx| 
|dbgrid32.ocx |Mscomm32.ocx |Msmapi32.ocx  |richtx32.ocx| 
|dblist32.ocx |Msdatgrd.ocx |Msmask32.ocx  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32.ocx| 
|msadodc.ocx  |msdatrep.ocx |MSRDO20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>No compatible, pero están disponibles las actualizaciones compatibles y compatibles

| | | | |
|---|---|---|---|
|Dao350.dll|   msexch35.dll| Msjter35.dll| Msrepl35.dll|
|Mdac_typ.exe| msexcl35.dll| Msjtor35.dll| Mstext35.dll|
|MSChart.ocx|  Msjet35.dll|  msltus35.dll| Msxbse35.dll|
|msdaerr.dll|  Msjint35.dll| Mspdox35.dll| Odbctl32.dll|
|msdatl2.dll|  Msjt4jlt.dll| MSRD2x35.dll| Oledb32x.dll|

## <a name="unsupported-runtime-files"></a>Archivos en tiempo de ejecución no compatible

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   Rpcltscm.dll|  RDOCURS.dll|
|graph32.ocx|  gauge32.ocx|  Rpcmqcl.dll|   Vbar332.dll|
|keysta32.ocx| gswdll32.dll| Rpcmqsvr.dll|  Visdata.exe|
|AUTMGR32.exe| ciscnfg.exe|  RPCSS.exe|     vsdbflex.srg|
|AUTPRX32.dll| Olecnv32.dll| Dbmsshrn.dll|  Threed32.ocx|
|RACMGR32.exe| RPCLTC1.dll|  dbmssocn.dll|  MSWLess.ocx|
|con RACREG32.dll| RPCLTC5.dll|  Windbver.exe|  tlbinf32.dll|
|grid32.ocx|   Rpcltccm.dll| msderun.dll|   Triedit.dll|
|msoutl32.ocx| RPCLTS5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>Archivos binarios de compatibilidad de localización

Los siguientes archivos binarios son necesarios para admitir aplicaciones de Visual Basic 6.0 que se ejecutan en las versiones localizadas del sistema operativo Windows. Se admiten, pero no se incluye en Windows. Estos archivos son necesarios para enviar con el programa de instalación de la aplicación.

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>Archivos de tiempo de ejecución admitidas para distribuir con la aplicación

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|

