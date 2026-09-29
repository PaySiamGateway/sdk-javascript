'use strict';


import { init } from './gatewayCfg.js';

import { deposit, depositAsync, withdraw, withdrawAsync, detail, detailAsync } from './gatewaySdk.js';


/**
 * Here is an example of a gateway sdk
 */
 

export async function test() {

    // initialize this configuration
    
    // apiUrl gateway Api Url
    
    // appId in developer settings : App Id
    
    // key in developer settings : Key
    
    // secret in developer settings : secret
    
    // serverPubKey in developer settings : Server Public Key
    
    // privateKey in developer settings : Private Key
    
    init(apiUrl, appId, key, secret, serverPubKey, privateKey);

    // Here is an example of a deposit 
    
    // return deposit result: code=1,message=,transactionId=12817291,paymentUrl=https://www.xxxx...
    
    deposit("10001", 100.00, "THB", "BANK_QRCODE", "gateway Test", "gateway@hotmail.com", "0812345678", (result) => {
        console.log("deposit result:", result);
    });

    // Here is an example of a withdraw
    
    // return withdraw result: code=1,message=,transactionId=12817291
    
    withdraw("10012", 100.00, "THB", "PROMPTPAY_MOBILE", "gateway Test", "0812345678", "", "gateway@hotmail.com", "0812345678", (result) => {
        console.log("withdraw result:", result);
    });

    // Here is an example of a detail
    
    // return detail result: code,message,transactionId,amount,fee
    
    detail("10024", 2, (result) => {
        console.log("detail result:", result);
    });

    // Here is an example of an async deposit 
    
    let depositResult = await depositAsync("10001", 100.00, "THB", "BANK_QRCODE", "gateway Test", "gateway@hotmail.com", "0812345678");
    
    console.log("async deposit result:", depositResult);

    // Here is an example of a async withdraw 
    
    let withdrawResult = await withdrawAsync("10012", 100.00, "THB", "PROMPTPAY_MOBILE", "gateway Test", "0812345678", "", "gateway@hotmail.com", "0812345678");
    
    console.log("async withdraw result:", withdrawResult);

    // Here is an example of a async detail 
    
    let detailResult = await detailAsync("10024", 2);
    
    console.log("async withdraw result:", detailResult);
}
