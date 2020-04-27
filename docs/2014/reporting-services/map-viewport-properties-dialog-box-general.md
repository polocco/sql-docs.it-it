---
title: Finestra di dialogo Proprietà viewport mappa, generale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8ec0aaa051ba317cd05a9784c80fb997f5fa19e6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108239"
---
# <a name="map-viewport-properties-dialog-box-general"></a>Finestra di dialogo Proprietà viewport mappa, Generale
  Selezionare **Generale** nella finestra di dialogo **Proprietà viewport mappa** per modificare le opzioni del sistema di coordinate, della proiezione e dei limiti.  
  
## <a name="options"></a>Opzioni  
 **Sistema di coordinate**  
 Indicare il tipo di sistema di coordinate utilizzato dai dati della mappa.  
  
-   **Planare** Scegliere questa opzione quando i dati della mappa sono espressi con le coordinate X e Y, ad esempio per la compilazione di piani.  
  
-   **Geografico** Scegliere questa opzione quando i dati della mappa sono espressi con le coordinate della longitudine e della latitudine, ad esempio per la posizione delle città.  
  
 **Proiezione**  
 Specificare il metodo da utilizzare per proiettare le coordinate geografiche su una superficie bidimensionale. Scegliere una proiezione compatibile con i dati che si stanno visualizzando. Le quattro proprietà spaziali interessate dalla proiezione sono area, forma, distanza e direzione. Per le viste della terra, la scelta di una proiezione ottimale dipende dalla vista con allineamento al centro, dai limiti della mappa e dal fattore di zoom.  
  
 Ognuna delle proiezioni seguenti mantiene almeno una di queste proprietà spaziali:  
  
-   **Equirettangolare** Scegliere questa opzione per utilizzare longitudine e latitudine come coordinate rettangolari.  
  
-   **Mercator** Scegliere questa proiezione comune per le aree più piccole, per una minor distorsione attorno all'equatore o quando si desidera aggiungere un livello mappa con un livello sezione esistente che utilizza la proiezione Mercator.  
  
-   **Robinson** Scegliere questa opzione per una minor distorsione delle aree grandi che si estendono dall'equatore ai poli. Sviluppata da Arthur H. Robinson nel 1963.  
  
-   **Fahey** Scegliere questa opzione per una minor distorsione delle aree grandi che si estendono dall'equatore ai poli. Sviluppata da Lawrence Fahey nel 1975.  
  
-   **Eckert1** Scegliere questa opzione per utilizzare paralleli equidistanti in latitudine e linee rette per i meridiani in longitudine.  
  
-   **Eckert3** Scegliere questa opzione per utilizzare paralleli equidistanti in latitudine e linee curve per i meridiani in longitudine.  
  
-   **HammerAitoff** Scegliere questa opzione per le mappe polari o del mondo.  
  
-   **Wagner3** Scegliere questa opzione per le mappe del mondo.  
  
-   **Bonne** Scegliere questa opzione per visualizzare il mondo come è presentato in un atlante.  
  
 **Opzioni di interruzione pagina**  
 Selezionare le opzioni per indicare il modo in cui il contenuto viene adattato alla pagina di un report.  
  
 **Opzioni relative ai limiti**  
 Specificare i limiti inferiore e superiore affinché le coordinate controllino quale parte della mappa viene visualizzata nel report.  
  
 **X minimo**  
 Valore X minimo. Disponibile solo per **Planare** .  
  
 **X massimo**  
 Valore X massimo. Disponibile solo per **Planare** .  
  
 **Y minimo**  
 Valore Y minimo. Disponibile solo per **Planare** .  
  
 **Y massimo**  
 Valore Y massimo. Disponibile solo per **Planare** .  
  
 **Longitudine minima**  
 Valore della longitudine minimo. Disponibile solo per **Geografico** .  
  
 **Longitudine massima**  
 Valore della longitudine massimo. Disponibile solo per **Geografico** .  
  
 **Latitudine minima**  
 Valore della latitudine minimo. Disponibile solo per **Geografico** .  
  
 **Latitudine massima**  
 Valore della latitudine massimo. Disponibile solo per **Geografico** .  
  
## <a name="see-also"></a>Vedi anche  
 [Mappe &#40;Generatore report e SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)  
  
  
