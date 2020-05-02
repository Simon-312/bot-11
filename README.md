# bot-for-my-cat

import vk_api
import vk_api
import random

#токен бота для кисоньки
token = "e132b7a0acfee6b05be229bc55be8b49587a707f2426287c03fafb40c6ef0764216c71ab584cad08fcc55"


vk = vk_api.VkApi(token=token)

vk._auth_token()

dz = "дз нет"
while True:
    try:
        messages = vk.method("messages.getConversations", {"offset": 0, "count": 20, "filter": "unanswered"})
        if messages["count"] >= 1:
            id = messages["items"][0]["last_message"]["from_id"]
            body = messages["items"][0]["last_message"]["text"]
            if "прив" in body.lower() or 'доброе' in body.lower() :
                vk.method("messages.send", {"peer_id": id, "message": "Привет! Я люблю кисоньку", "random_id": random.randint(1, 2147483647)})
            elif body.lower() == "кто я?":
                vk.method("messages.send", {"peer_id": id, "message": "ты моё милое солнышко", "random_id": random.randint(1, 2147483647)})
            elif 'мур' in body.lower() or 'муу' in body.lower(): #МУРЧАНИЕ
                Q=random.randint(1,4)
                if Q<3:
                    vk.method("messages.send", {"peer_id": id, "message": "люблю когда милашка мурчит", "random_id": random.randint(1, 2147483647)})
                elif Q==3:
                    vk.method("messages.send", {"peer_id": id, "message": "моё милое мурчало","random_id": random.randint(1, 2147483647)})
            elif "приятн" in body.lower():
                vk.method("messages.send", {"peer_id": id, "message": "И котику тоже очень приятно", "random_id": random.randint(1, 2147483647)})
            elif "любл" in body.lower():   #ЛЮБЛЮ ТЕБЯ ОТВЕТЫ С ВЕРОЯТНОСТЬЮ
                Q = random.randint(1,6)
                if Q < 3:
                    vk.method("messages.send", {"peer_id": id, "message": "А я тебя больше люблю:3","random_id": random.randint(1, 2147483647)})
                elif Q == 3:
                    vk.method("messages.send", {"peer_id": id, "message": "И я тебя люблю мой ангелочек","random_id": random.randint(1, 2147483647)})
                elif Q>3:
                    vk.method("messages.send", {"peer_id": id, "message": "Я кисоньку тоже очень сильно люблю", "random_id": random.randint(1, 2147483647)})
            elif "нет" in body.lower():
                vk.method("messages.send", {"peer_id": id, "message": "Дяяяя", "random_id": random.randint(1, 2147483647)})
            elif "приятн" in body.lower():
                vk.method("messages.send", {"peer_id": id, "message": "И котику тоже очень приятно", "random_id": random.randint(1, 2147483647)})
            elif "груст" in body.lower() or "плак" in body.lower() or "плач" in body.lower():
                vk.method("messages.send", {"peer_id": id, "message": "Не грусти маленькая кисонька", "random_id": random.randint(1, 2147483647)})
            elif "хихи" in body.lower():
                vk.method("messages.send", {"peer_id": id, "message": "Кисюндра смешная и приятная","random_id": random.randint(1, 2147483647)})
            elif 'мя' in body.lower() or 'миу' in body.lower():  # МЯУКАНЬЕ
                vk.method("messages.send", {"peer_id": id, "message": "тю котёночек мяукает", "random_id": random.randint(1, 2147483647)})
            elif "глад" in body.lower():
                vk.method("messages.send", {"peer_id": id, "message": "поглажу маленькую кисю", "random_id": random.randint(1, 2147483647)})
            elif "целу" in body.lower():
                vk.method("messages.send", {"peer_id": id, "message": "поцелую тебя моё солнышко", "random_id": random.randint(1, 2147483647)})
            elif "обним" in body.lower():
                vk.method("messages.send", {"peer_id": id, "message": "обниму и не путю", "random_id": random.randint(1, 2147483647)})
            elif "хо" in body.lower() and " к " in body.lower():  #ХОЧУ К ТЕБЕ И ТД
                vk.method("messages.send", {"peer_id": id, "message": "я к тебе тоже очень хотю моя родная", "random_id": random.randint(1, 2147483647)})




            else:    # ТУТ БОТ ОТВЕЧАЕТ НА ТО ЧТО НЕ ПОНИМАЕТ
                x=random.randint(1,6)
                if x==1:
                    vk.method("messages.send", {"peer_id": id, "message": "я не знаю что значит " + str(body.lower())+ ', но я люблю кисоньку', "random_id": random.randint(1, 2147483647)})
                elif x==2:
                    vk.method("messages.send", {"peer_id": id, "message": "Я не понял эту фразу солнышко, дявай лучше что нибудь милое","random_id": random.randint(1, 2147483647)})
                elif x==3:
                    vk.method("messages.send", {"peer_id": id, "message": "Прости что я не всё понимаю, но ти можешь обсудить это с котиком","random_id": random.randint(1, 2147483647)})
                elif x>3:
                    vk.method("messages.send", {"peer_id": id, "message": "я не понимаю что такое " + str(body.lower()) + ', но я обниму кисоньку и кися улыбнётся', "random_id": random.randint(1, 2147483647)})
    except Exception as E:
        time.sleep(10)


