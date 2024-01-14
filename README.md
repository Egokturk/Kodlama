# Kodlama
Kodlamayi böyle ögrenebilirsin
Bu sana kodlamayi örenmene yardimci olacak bir link https://womaneng.com/10-adimda-kodlamayi-ogrenme/

BUda sana script yazmayi öretecek
https://www.google.com/search?q=how+to+create+scripts+in+pc&sca_esv=598417864&rlz=1CASACE_enAT1033AT1033&ei=ayWkZcvpFau3i-gPtJG1iAw&ved=0ahUKEwiLy-Xfvt2DAxWr2wIHHbRIDcEQ4dUDCBA&uact=5&oq=how+to+create+scripts+in+pc&gs_lp=Egxnd3Mtd2l6LXNlcnAiG2hvdyB0byBjcmVhdGUgc2NyaXB0cyBpbiBwYzIFECEYoAEyBRAhGKABMgUQIRigAUjAM1CHEFj3LnABeACQAQCYAbIBoAGQCKoBAzAuN7gBA8gBAPgBAcICChAAGEcY1gQYsAPCAgcQABiABBgTwgIIEAAYFhgeGBPiAwQYACBBiAYBkAYI&sclient=gws-wiz-serp&safe=active&ssui=on#fpstate=ive&vld=cid:11bc0f38,vid:lYqaldXFm1U,st:0

BU sana script yazmakla gereken bilgileri vericek    https://www.ionos.at/digitalguide/server/konfiguration/powershell-script-erstellen/

Burdada benim yazdigim bazi scriptlr var istersen kullan ;) 

Bu Typingclub icin 

 /**
 * This script types for you automatically on www.typingclub.com:
 * 1. Open the website
 * 2. Blaze past the tutorials
 * 3. Go into a level
 * 4. Open Console
 * 5. Paste the script and press ENTER
 */

// NOTE: When delay (in ms between two strokes) is too low, the site might bug out and the result page will not be shown
const minDelay = 60;
const maxDelay = 60;



const keyOverrides = {
  [String.fromCharCode(160)]: ' '    // convert hardspace to normal space
};

function getTargetCharacters() {
  const els = Array.from(document.querySelectorAll('.token span.token_unit'));
  const chrs = els
    .map(el => {
      // get letter to type from each letter DOM element
      if (el.firstChild?.classList?.contains('_enter')) {
        // special case: ENTER
        return '\n';
      }
      let text = el.textContent[0];
      return text;
    })
    .map(c => keyOverrides.hasOwnProperty(c) ? keyOverrides[c] : c); // convert special characters
  return chrs;
}

function recordKey(chr) {
  // send it straight to the internal API
  window.core.record_keydown_time(chr);
}

function sleep(ms) {
  return new Promise(r => setTimeout(r, ms));
}

async function autoPlay(finish) {
  const chrs = getTargetCharacters();
  for (let i = 0; i < chrs.length - (!finish); ++i) {
    const c = chrs[i];
    recordKey(c);
    //console.log(c, c.charCodeAt());
    await sleep(Math.random() * (maxDelay - minDelay) + minDelay);
  }
}

// ############################################################################################################
// old utilities
// ############################################################################################################


// /**
//  * @see https://stackoverflow.com/questions/8942678/keyboardevent-in-chrome-keycode-is-0/12522752#12522752
//  */
// function simulateKey(chr, el) {
//   _simulateKey(chr, 'keydown', el);
//   _simulateKey(chr, 'keypress', el);
// }
// function _simulateKey(chr, type, el) {
//   var eventObj = document.createEventObject ?
//     document.createEventObject() : document.createEvent("Events");

//   if (eventObj.initEvent) {
//     eventObj.initEvent(type || "keydown", true, true);
//   }

//   let keyCode = chr.charCodeAt(0);

//   eventObj.key = chr[0];
//   eventObj.keyCode = keyCode;
//   eventObj.which = keyCode;
//   eventObj.isTrusted = true;

//   el = el || document.body;

//   // console.log(keyCode, eventObj);

//   el.dispatchEvent ? el.dispatchEvent(eventObj) : el.fireEvent("onkeydown", eventObj); 
// }

// document.addEventListener("keydown", function (e) {
//   console.log('down', e);
// });
// document.addEventListener("keypress", function (e) {
//   console.log('press', e);
// });
//$($('.menu-btn')[0].parentNode).prepend('<button onclick=\'simulateKeyPress("c")\'>sim</button>');
// simulateKey('a', $('input')[0]);



// ############################################################################################################
// go!
// ############################################################################################################

autoPlay(true);

Buda Canvva icin 

import asyncio
from pyppeteer import launch

async def main():
    # Launch a new browser instance
    browser = await launch(headless=True)
    # Create a new page
    page = await browser.newPage()
    # Set the user agent
    await page.setUserAgent('Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.67 Safari/537.36')
    # Navigate to the website
    await page.goto("https://bingotingo.com/best-social-media-platforms/")
    # Wait for the element with the text "Free Guide" to load
    await page.waitForXPath("//h2[text()='Free Guide']")
    # Scroll down until the element with the text "Script link" is found
    await page.xpath("//h2[text()='Free Guide']")
    # Wait for the button to appear and be clickable
    print("Trying to find canva pro for you! Please wait 60s...")
    await page.waitForXPath("//*[@id='download']", {'visible': True, 'timeout': 70000})
    button = await page.xpath("//*[@id='download']")
    # Click the button that opens the new tab
    await button[0].click()
    # Wait for the new tab to open
    await asyncio.sleep(5)
    # Get the handle of the new tab
    new_tab = (await browser.pages())[-1]
    # Switch to the new tab
    await new_tab.bringToFront()
    # Extract the href link from the button
    href_link = await new_tab.xpath("//a[text()='GET HERE']")
    href_link = await (await href_link[0].getProperty('href')).jsonValue()
    #Print the link of canva pro in a text file
    with open("canva_pro_link.txt", "w") as f:
        f.write(href_link)
        print("Canva Pro Found!")

    # Close the browser instance
    await browser.close()

asyncio.get_event_loop().run_until_complete(main())
