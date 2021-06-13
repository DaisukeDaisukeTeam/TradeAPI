# TradeAPI
<b>Implement Trade V2 UI in PMMP</b>  
https://github.com/organization/TradeAPI
# note: This fork has a bug

## How to use
> [Youtube](https://youtu.be/38xiaMfrlcU)

> Registrant virion
```php
if (!TradeHandler::isRegistrant()) {
    TradeHandler::register($this);
}
```
```php
use nlog\trade\merchant\MerchantRecipe;
use nlog\trade\merchant\MerchantRecipeList;
use nlog\trade\merchant\TradeProperties;
use nlog\trade\TradeAPI;
use nlog\trade\TradeHandler;
use pocketmine\event\server\DataPacketReceiveEvent;
use pocketmine\item\enchantment\Enchantment;
use pocketmine\item\enchantment\EnchantmentInstance;
use pocketmine\item\ItemFactory;
use pocketmine\item\ItemIds;
```
```php
$prop = new TradeProperties();
$prop->maxTradeTier = 3;
$prop->tradeTier = 2;
$prop->tradeName = "[Test] Trade API";
$prop->xp = intval($args[0] ?? mt_rand(0, 50));

$item = ItemFactory::get(ItemIds::ENCHANTED_BOOK);
$item->addEnchantment(new EnchantmentInstance(Enchantment::getEnchantment(Enchantment::PROTECTION),4));
$item1 = ItemFactory::get(ItemIds::BOOK);
$item1->addEnchantment(new EnchantmentInstance(Enchantment::getEnchantment(Enchantment::MENDING), 0));
TradeHandler::getTradeAPI()->sendWindow($sender,new MerchantRecipeList(
	new MerchantRecipe(ItemFactory::get(ItemIds::ROTTEN_FLESH, 0, 32), ItemFactory::get(ItemIds::EMERALD), null, 0),
	new MerchantRecipe(ItemFactory::get(ItemIds::GOLD_NUGGET, 0, 32), ItemFactory::get(ItemIds::EMERALD), null, 0),
	new MerchantRecipe(ItemFactory::get(ItemIds::COAL, 0, 16), ItemFactory::get(ItemIds::EMERALD), null, 0),
	new MerchantRecipe(ItemFactory::get(ItemIds::DIAMOND, 0, 16), ItemFactory::get(ItemIds::EMERALD)->setCustomName("§bTrade"), null, 1),


	new MerchantRecipe(ItemFactory::get(ItemIds::EMERALD, 0, 52), $item, ItemFactory::get(ItemIds::BOOK), 2),
	new MerchantRecipe(ItemFactory::get(ItemIds::EMERALD, 0, 64), $item, ItemFactory::get(ItemIds::BOOK),3),
), $prop);
```

## LICENSE
* 이 플러그인 또는 플러그인 코드를 사용하는 경우 AGPL 라이선스에 동의하는 것으로 간주합니다.
* By using this plugin or plugin code, you agree to the AGPL license.
```
TradeAPI, simple to provide Trade UI V2.
Copyright (C) 2020  Organic (nnnlog)

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```

### TODO
* [ ] 올바른 교환인지 검증
* [ ] FakeInventory 검증
* [ ] API Docs
