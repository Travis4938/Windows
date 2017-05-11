# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag

```objectivec

#import <Foundation/Foundation.h>
#import "IMegaController.h"
#import "MegaUtil.h"

typedef NS_ENUM(NSUInteger, MegamDongleUnitInfoType){
    MegamDongleUnitInfoTypeModel = 0x00,
    MegamDongleUnitInfoTypeSerialNumber = 0x01,
    MegamDongleUnitInfoTypeManufacturer = 0x02,
    MegamDongleUnitInfoTypeFirmwareTimestamp = 0xA0,
};

typedef NS_ENUM(NSUInteger, MegamDongleUnit){
    MegamDongleUnitHost = 0x00,
    MegamDongleUnitSlave = 0x01,
};

typedef NS_ENUM(NSUInteger, MegamDongleNfcCardType){
    MegamDongleNfcCardTypeInvalidCarDetected = 0x0000,
    MegamDongleNfcCardTypeMIFAREUltralight   = 0x0001,
    MegamDongleNfcCardTypeMIFAREClassic      = 0x0003,
};

@protocol IMegamDongleControllerDelegate;

@protocol IMegamDongleController <IMegaController>
@property(nonatomic, weak, nullable) id<IMegamDongleControllerDelegate> delegate;
-(void) getInfomation:(MegamDongleUnitInfoType)unitInfoType inUnit:(MegamDongleUnit)unit;
-(void) readNfcCardType;
-(void) readNfcUid:(MegamDongleNfcCardType)cardType;

@end

@protocol IMegamDongleControllerDelegate <NSObject>
@optional
-(void) mDongleController:(nonnull id<IMegamDongleController>)controller readUnitInfo:(nonnull NSDictionary*)info  error:(nullable NSError*)error;
-(void) mDongleController:(nonnull id<IMegamDongleController>)controller readNfcCardType:(MegamDongleNfcCardType)cardType  error:(nullable NSError*)error;
-(void) mDongleController:(nonnull id<IMegamDongleController>)controller readNfcUid:(nonnull NSString*)uid error:(nullable NSError*)error;



@end

```

If you want to embed images, this is how you do it:

![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)
