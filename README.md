# manite
Tel
<?php
/*
به نام خداوند بخشنده ی مهربان
*/
define('API_KEY','402202314:AAGN48JQiEHMdcyCCvA9LFT0EdTHhpYHMYE');
//##############
function makereq($method,$datas=[]){
	$API_BOT = CURLOPT_POSTFIELDShttp_build_true;
    curl_setopt($ch,CURLOPT_URL,$url);
    curl_setopt($ch,CURLOPT_RETURNTRANSFER,true);
    curl_setopt($ch,CURLOPT_POSTFIELDS,http_build_query($datas));
    $res = curl_exec($ch);
    if(curl_error($ch)){
        var_dump(curl_error($ch));
    }else{
        return json_decode($res);
    }
}
//##############=--API_REQ
function apiRequest($method, $parameters) {
  if (!is_string($method)) {
    error_log("Method name must be a string\n");
    return fals;
  }
  if (!$parameters) {
    $parameters = array();
  } else if (!is_array($parameters)) {
    error_log("Parameters must be an array\n");
    return false;
  }
  foreach ($parameters as $key => &$val) {
    // encoding to JSON array parameters, for example reply_markup
    if (!is_numeric($val) && !is_string($val)) {
      $val = json_encode($val);
    }
  }
  $url = "https://api.telegram.org/bot".API_KEY."/".$method.'?'.http_build_query($parameters);
  $handle = curl_init($url);
  curl_setopt($handle, CURLOPT_RETURNTRANSFER, true);
  curl_setopt($handle, CURLOPT_CONNECTTIMEOUT, 5);
  curl_setopt($handle, CURLOPT_TIMEOUT, 60);
  return exec_curl_request($handle);
}
//----######------
//---------
$update = json_decode(file_get_contents('php://input'));
var_dump($update);
//=========
$chat_id = $update->message->chat->id;
$message_id = $update->message->message_id;
$from_id = $update->message->from->id;
$username = $update->message->from->username;
$textmessage = isset($update->message->text)?$update->message->text:'';
$admin = 348309680;
$step = file_get_contents("data/".$from_id."/step.txt");
$bots = file_get_contents("data/".$from_id."/bots.txt");
$bottoken = file_get_contents('data/'.$from_id.'/token.txt');
$tedad = file_get_contents("data/".$from_id."/tedad.txt");
$host_folder = "http://thekingteam.cf/antispamsaz/";
//-------
function SendMessage($ChatId, $TextMsg)
{
 makereq('sendMessage',[
'chat_id'=>$ChatId,
'text'=>$TextMsg,
'parse_mode'=>"MarkDow"
]);
}
function Forward($KojaShe,$AzKoja,$KodomMSG)
{
makereq('ForwardMessage',[
'chat_id'=>$KojaShe,
'from_chat_id'=>$AzKoja,
'message_id'=>$KodomMSG
]);
}
function save($filename,$TXTdata)
	{
	$myfile = fopen($filename, "w") or die("Unable to open file!");
	fwrite($myfile, "$TXTdata");
	fclose($myfile);
	}
//===========
if ($textmessage == '🔙برگشت به منو اصلی🔙') {
save("data/$from_id/step.txt","none");
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"🆗شما به منو اصلی برگشتید🆗",
		'parse_mode'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'keyboard'=>[
                [
                ['text'=>"🛠ساخت ربات🛠"],['text'=>"🤖ربات های من🤖"]
                ],
                [
				['text'=>"🗑حذف ربات🗑"]
				],
				[
                ['text'=>"‼️راهنما استفاده از ربات‼️"]
                ],
                [
                ['text'=>"📞پشتیبانی📞"],['text'=>"📝قوانین استفاده از ربات📝"]
                ],
                [
                ['text'=>"🔧سازنده ربات🔧"],['text'=>"⁉️سوالات متداول⁉️"]
                ],
            	'resize_keyboard'=>true
       		]
    		]
			
elseif ($step == ('create bot') 
$token = $textmessage ;

			$userbot = json_decode(file_get_contents('https://api.telegram.org/bot'.$token .'/getme'));
			//==================
			function objectToArrays( $object ) {
				if( !is_object( $object ) && !is_array( $object ) )
				{
				return $object;
				}
				if( is_object( $object ) )
				{
				$object = get_object_vars( $object );
				}
			return array_map( "objectToArrays", $object );
			}

	$resultb = objectToArrays($userbot);
	$un = $resultb["result"]["username"];
	$ok = $resultb["ok"];
		if($ok != 1) {
			//Token Not True
			SendMessage($chat_id,"🚫توکن شما نامعتبر است🚫");
		}
		else
		{
		save("data/$from_id/tedad.txt","1");
		save("data/$from_id/step.txt","none");
		save("data/$from_id/bots.txt","$un");
		save("data/$from_id/token.txt","$token");
		SendMessage($chat_id,"در حال ساخت ربات...✅");
		mkdir("bots/$un");
		mkdir("bots/$un/data");
		mkdir("bots/$un/data/admin");
		save("bots/$un/data/admin/step.txt","none");
		save("bots/$un/users.txt","");
		save("bots/$un/groups.txt","");
		save("bots/$un/supergroups.txt","");
		save("bots/$un/data/admins.txt","");
		save("bots/$un/data/admins.txt","$from_id");		
		$source = file_get_contents("bot/index.php");
		$source = str_replace("[TOKEN]",$token,$source);
		$source = str_replace("[ADMIN]",$from_id,$source);
		save("bots/$un/index.php",$source);	
file_get_contents("https://api.telegram.org/bot".$token."/setwebhook?url=https://$host_folder/bots/$un/index.php");
		var_dmp(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"برای ورود به ربات روی دکمه زیر کلیک کنید👇👍\nربات شما با موفقیت ایجاد شد✔️",
        	'parse_mde'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'inline_keyboard'=>[
                [
                ['text'=>"@$un",'url'=>"https://t.me/$un"]
                ]
            	]
       		])
    		]));
		}
var_dump(makereq('sendMessage',[
        	'chat_userid'=>$update->message->chat->id,
        	'text'=>"🆗شما به منو اصلی برگشتید🆗",
		'parse_mode'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'keyboard'=>[
                [
                ['text'=>"🛠ساخت ربات🛠"],['text'=>"🤖ربات های من🤖"]
                ],
				[
                ['text'=>"🗑حذف ربات🗑"]
                ],
                [
                ['text'=>"‼️راهنما استفاده از ربات‼️"],['text'=>"📞پشتیبانی📞"],['text'=>"📝قوانین استفاده از ربات📝"]
                ],
                [
                ['text'=>"🔧سازنده ربات🔧"],['text'=>"⁉️سوالات متداول⁉️"]
                ]
            	],
            	'resize_keyboard'=>true
       		])
    		]));
    		save("data/$from_id/step.txt","none");
}
$chn = "teamking_sh";
$sudouser = "the_king_team_creator";
$kirkhar = file_get_contents("https://api.telegram.org/bot".API_KEY."/getChatMember?chat_id=@$chn&user_id=$from_id");
 
 if (strpos($kirkhar , '"status":"left"') !== false ) {
var_dump(makereq('sendmessage',[
        'chat_id'=>$update->message->chat->id,
        'text'=>"سلام ✋️

برای استفاده از ربات عضو شدن در کانال ما اجباری می باشد😏👌

بعد از این که عضو کانال شدید به ربات بگردید و دستور زیر را ارسال کنید🙃👌

😑👇

🎗 /start 🎗",
 'parse_mode'=>'MarkDown',
        'reply_markup'=>json_encode([
            'inline_keyboard'=>[
                [
                    ['text'=>"ورود به کانال",'url'=>"https://telegram.me/$chn"]
                ]
            ]
        ])
    ]));
}

elseif($textmessage == '/start')
{

if (!file_exists("data/$from_id/step.txt")) {
mkdir("data/$from_id");
save("data/$from_id/step.txt","none");
save("data/$from_id/tedad.txt","0");
$myfile2 = fopen("data/users.txt", "a") or die("Unable to open file!");	
fwrite($myfile2, "$from_id\n");
fclose($myfile2);
}

var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"سلام دوباره🙃✋️

به ربات ساخت ربات آنتی اسپم پیشرفته خوش آمدی❤️🌹

شما هم با این ربات ، ربات آنتی اسپم پیشرفته بسازید و گروه خود و گروه دیگران را به ربات انتی اسپم مجهز کنید😇

🛠سازنده ربات🛠 :
$sudo_user | $chn",
		'parse_mode'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'keyboard'=>[
                [
                ['text'=>"🛠ساخت ربات🛠"],['text'=>"🤖ربات های من🤖"]
                ],
                [
                ['text'=>"🗑حذف ربات🗑"]
                ],
                [
                ['text'=>"‼️راهنما استفاده از ربات‼️"],['text'=>"📞پشتیبانی📞"],['text'=>"📝قوانین استفاده از ربات📝"]
                ],
                [
                ['text'=>"🔧سازنده ربات🔧"],['text'=>"⁉️سوالات متداول⁉️"]
                ]
            	],
            	'resize_keyboard'=>true
       		])
    		]));
}
elseif ($textmessage == '🛠ساخت ربات🛠') {
save("data/$from_id/step.txt","create bot");
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"به بخش ساخت ربات آنتی اسپم پیشرفته خوش آمدید

توکن خود را از ربات @botgfather بدون چیز اضافی ارسال کنید تا ربات رو بسازم👌🤝",
		'parse_mode'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'keyboard'=>[
                [
                   ['text'=>"🔙برگشت به منو اصلی🔙"]
                ]
                
            	],
            	'resize_keyboard'=>true
       		])
    		]));
}
elseif ($textmessage == '🗑حذف ربات🗑') {
    if (file_exists("data/$from_id/bots.txt")) {
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"رباتی که میخواهید حذف کنید را انتخاب کنید😕 حذفش نکن😭",
		'parse_mode'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'keyboard'=>[
				[
                   ['text'=>"@$bots ❌"]
                ],
                [
                   ['text'=>"🔙برگشت به منو اصلی🔙"]
                ]
                
            	],
            	'resize_keyboard'=>true
       		])
    		]));
}else
{
    	SendMessage($chat_id,"تو سرور من اصلا رباتی به اسمت نیست😐🎈");
}
}
elseif ($textmessage == "@$bots ❌") {
        if (file_exists("data/$from_id/bots.txt")) {
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"⭕️ آیا مطمئن هستید ربات شما با آیدی @$bots حذف شود؟",
		'parse_mode'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'keyboard'=>[
                [
                ['text'=>"بله کاملا مطمئنم حذفش کن❌"]
                ],
                [
                ['text'=>"نه پشیمون شدم برگرد به صفحه اصلی🙂👈"]
                ]
            	],
            	'resize_keyboard'=>true
       		])
    		]));
}else
{
    	SendMessage($chat_id,"تو سرور من اصلا رباتی به اسمت نیست😐🎈");
}
}
elseif ($textmessage == "بله کاملا مطمئنم حذفش کن❌") {
        if (file_exists("data/$from_id/bots.txt")) {
	unlink("bots/$bots/index.php");
	unlink("bots/$bots/users.txt");
	unlink("bots/$bots/groups.txt");
	unlink("bots/$bots/supergroups.txt");
	unlink("bots/$bots/data/admins.txt");
	unlink("bots/$bots/data/admin/step.txt");
	rmdir("bots/$bots/data/admin");
	rmdir("bots/$bots/data");
	rmdir("bots/$bots");
	unlink("data/$from_id/bots.txt");
	file_get_contents("https://api.telegram.org/bot".$bottoken."/setwebhook");
	save("data/$from_id/tedad.txt","0");
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"مطمئن باش رباتت کاملا حذف شد✅ راحت شدی❓",
		'parse_mode'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'keyboard'=>[
                [
                ['text'=>"🛠ساخت ربات🛠"],['text'=>"🤖ربات های من🤖"]
                ],
                [
                ['text'=>"🗑حذف ربات🗑"]
                ],
                [
                ['text'=>"‼️راهنما استفاده از ربات‼️"],['text'=>"📞پشتیبانی📞"],['text'=>"📝قوانین استفاده از ربات📝"]
                ],
                [
                ['text'=>"🔧سازنده ربات🔧"],['text'=>"⁉️سوالات متداول⁉️"]
                ]
            	],
            	'resize_keyboard'=>true
       		])
    		]));
}else
{
    	SendMessage($chat_id,"تو سرور من اصلا رباتی به اسمت نیست😐🎈");
}
}
elseif ($textmessage == '📞پشتیبانی📞') {
save("data/$from_id/step.txt","feedback");
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"پیامی که میخوای به پشتیبانی بفرستی بنویس🖊 زود باش حوصله ندارم😤.",
		'parse_mode'=>'MarkDown',
        	'reply_markup'=>json_encode([
            	'keyboard'=>[
                [
                   ['text'=>"🔙برگشت به منو اصلی🔙"]
                ]
                
            	],
            	'resize_keyboard'=>true
       		])
    		]));
}
elseif ($step == 'feedback') {
    save("data/$from_id/step.txt","none");
	SendMessage($chat_id,"پیام شما مستقیم به دست پشتیبانی رسید👌😐حالا میزاری راحت بشینیم😑.");
		SendMessage($admin,"نظر جدید:\n$textmessage\n$username");
}
elseif ($textmessage == '🔧سازنده ربات🔧') {
	SendMessage($chat_id,"$sudo_user");
}
elseif($textmessage == '/creator'){
	Sendmessage($chat_id,"Created By $sudo_user");
}
elseif($textmessage == '/Creator'){
	Sendmessage($chat_id,"Created By $sudo_user");
}
elseif ($textmessage == '‼️راهنما استفاده از ربات‼️') {
	SendMessage($chat_id,"
	 لیست راهنما ربات های ساخته شده توسط این بات :
>راهنمای بخش دریافت تنظیمات و مدیریت کاربران
[/]manage ➖ (دریافت تنظیات ربات به صورت اینلاین)
[/]kick |reply| ➖ (اخراج کاربر با ریپلی)
➖➖➖➖➖➖
>راهنمای دستورات مدیریتی
[/]lock|unlock link ➖ (فعال سازی/غیرفعال سازی قفل ارسال لینک)
[/]lock|unlock username ➖ (فعال سازی/غیرفعال سازی قفل ارسال یوزرنیم)
[/]lock|unlock sticker ➖ (فعال سازی/غیرفعال سازی قفل ارسال استیکر)
[/]lock|unlock contact ➖ (فعال سازی/غیرفعال سازی قفل اشتراک گزاری شماره)
[/]lock|unlock forward ➖ (فعال سازی/غیرفعال سازی قفل ارسال فوروارد)
[/]lock|unlock photo ➖ (فعال سازی/غیرفعال سازی قفل ارسال تصویر)</code>
[/]lock|unlock audio ➖ (فعال سازی/غیرفعال سازی قفل ارسال موسیقی(Audio))
[/]lock|unlock voice ➖ (فعال سازی/غیرفعال سازی قفل ارسال صدا(Voice))
[/]lock|unlock edit ➖ (فعال سازی/غیرفعال سازی قفل ویرایش پیام)
[/]lock|unlock game ➖ (فعال سازی/غیرفعال سازی قفل انجام بازی در گروه)
[/]lock|unlock location ➖ (فعال سازی/غیرفعال سازی قفل اشتراک گزاری مکان)
[/]lock|unlock fosh ➖ (فعال سازی/غیرفعال سازی قفل فحاشی)
[/]lock|unlock join ➖ (فعال سازی/غیرفعال سازی قفل ورود به گروه)
[/]lock|unlock operator ➖ (فعال سازی/غیرفعال سازی قفل تبلیغات اوپراتورها)
[/]lock|unlock video ➖ (فعال سازی/غیرفعال سازی قفل ارسال ویدیو)
[/]lock|unlock bots ➖ (فعال سازی/غیرفعال سازی قفل ورود ربات ها)
➖➖➖➖➖➖
>راهنمای فلود
[/]flood manage ➖ (دریافت تنظیمات فلود به صورت اینلاین)
[/]lock|unlock flood ➖ (فعال سازی/غیرفعال سازی قفل فلود)
[/]setflood [Number] ➖ (تنظیم میزان فلود)
➖➖➖➖➖➖
>راهنمای حذف پیام
[/]rmsg [Number] ➖ (حذف پیام به تعداد معین (بین 0 و200))
➖➖➖➖➖➖
>راهنمای بخش خوش امدگویی
[/]welcome enable|disable  ➖ (فعال سازی/غیرفعال سازی عملیات خوش امدگویی)
[/]set welcome ➖ (تنظیم پیغام خوش امدگویی)
➖➖➖➖➖➖
>راهنمای دستورات جدید
➖➖➖➖➖➖
[/]setname [Name] ➖ (تنظیم نام گروه)
[/]setdescription [Text] ➖ (تنظیم توضیحات گروه)
[/]setphoto ➖ (تنظیم تصویر گروه)
[/]delphoto ➖ (حذف تصویر گروه)
[/]pin [reply] ➖ (پین کردن یک پیام با ریپلای)
[/]unpin [reply] ➖ (برداشتن پین با ریپلای)
[/]link ➖ (دریافت لینک گروه)
[/]setowner [TelegramID] ➖ (تغییر صاحب گروه با شناسه کاربری)
[/]automatic [manage] ➖ (مدیریت گروه به صورت خودکار توسط ربات)
");
}
elseif ($textmessage == '🤖ربات های من🤖') {
        if (file_exists("data/$from_id/bots.txt")) {
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"🤖 ربات های شما :\n➖➖➖➖➖➖\n@$bots\n➖➖➖➖➖➖",
		'parse_mode'=>'MarkDown'
]));
}else
{
    	SendMessage($chat_id,"عجیجم اصلا رباتی نداری ولمون کن☹️.");
}
}
elseif ($textmessage == '📝قوانین استفاده از ربات📝') {
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"❇️قوانین ساخت ربات :

			فقط اینو بهت بگم که:
فروش این رباتا ممنوعه جایی ببینمشون میگم پلیس بیاد دنبالت😡
اگه ببینم ربات +18 ساختی ها بازم میدمت دست پلیس😑
حله؟👌😐
🚀با تشکر از تیم :
@$chn",
		'parse_mode'=>'MarkDown'
		]));
}
elseif ($textmessage == '⁉️سوالات متداول⁉️') {
var_dump(makereq('sendMessage',[
        	'chat_id'=>$update->message->chat->id,
        	'text'=>"سوالاتی که خیلی وقتا میپرسین🙄👇

❇️آیا ربات های آنتی اسپمی که میسازیم همه میتونن استفاده کنند »
خیر فقط ادمین ربات {سازنده ربات} میتواند ربات را در گروهی فعال کند با دستور add/

❇️دستورات سودو ربات چیست  »
فروارد همگانی , پیام همگانی , آمار ربات , add , charge

❇️دستورات مدیریتی ربات در گروه چیست  »
/manage , /add , /help , /flood manage

❇️چگونه گروه رو شارژ کنیم ربات از گروه پس از اعتبار خارج شود »
/charge DAY , TIME
Creator : $sudo_user | @$chn",
		'parse_mode'=>'MarkDown'
		]));
}
elseif ($textmessage == "/panel" && $from_id == $admin){
var_dump(makereq('sendMessage',[
        'chat_id'=>$update->message->chat->id,
        'text'=>"`پنل مدیریت با موفقیت باز شد\nیکی از دکمه هارا انتخاب کنید :`",
        'parse_mode'=>'MarkDown',
        'reply_markup'=>json_encode([
            'keyboard'=>[
              [
                ['text'=>"پیام همگانی"],['text'=>"امار"]
              ]
            ],
        ])
    ]));  
	}
		elseif($textmessage == 'امار' && $chat_id == $admin)
	{
		$txtt = file_get_contents('data/users.txt');
		$membersidd= explode("\n",$txtt);
		$mmemcount = count($membersidd) -1;
{
sendmessage($chat_id,"`تعداد کل اعضای ربات :` $mmemcount");
}
}
	elseif($textmessage == '/send'){
	save("data/".$from_id."/step.txt","s2a");
	SendMessage($chat_id," پیامتون رو ارسال کنید ⚠ :");
	}
	elseif($step == 's2a'){
	save("data/".$from_id."/step.txt","none");
	SendMessage($chat_id," پیام شما در صف ارسال قرار گرفت. ✅");
	$all_member = fopen( "data/users.txt", 'r');
		while( !feof( $all_member)) {
 			$user = fgets( $all_member);
			if($textmessage != null){
			SendMessage($user,$textmessage);
			}else{
			SendMessage($chat_id,"فقط متن");
			}
		}
