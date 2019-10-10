```python
#1. 몬티홀
import random
n=int(input('문의 수를 입력하십시오\n'))
p=0
stay, stay_win, move, move_win = 0, 0, 0, 0
while p<300000:
    doors=list(range(1,n+1))
    know=list(range(1,n+1))
    
    car=random.choice(doors)
    choice=random.choice(doors)
    
    know.remove(car) #사회자는 차가 어디에 있는 알고 있다.
    if car != choice:
        know.remove(choice)
    open_door=random.choice(know)
    
    doors.remove(open_door)
    final_choice=random.choice(doors)
    
    if choice==final_choice: #가만히 있을 때의
        stay+=1
        if final_choice==car: #승리 확률과
            stay_win+=1
    else: #옮겼을 때의
        move+=1
        if final_choice==car : #승리 확률
            move_win+=1
    p+=1
print(round(stay/p,4), round(move/p,4)) #반올림 
print(stay_win/stay, move_win/move) #만약 n=5 이면, 1/5과 4/15가 나온다.
```
```python
#2. 사회자는 차가 있는 곳을 모름
import random
n=int(input('문의 수를 입력하십시오\n'))
p=0
stay, stay_win, move, move_win = 0, 0, 0, 0
mistake=0
while p<300000:
    doors=list(range(1,n+1))
    know=list(range(1,n+1))
    
    car=random.choice(doors)
    choice=random.choice(doors)
    
    know.remove(choice)
    open_door=random.choice(know)
    
    doors.remove(open_door) #사회자는 차의 위치를 모른다.
    final_choice=random.choice(doors)
    
    if open_door==car: #사회자가 차가 있는 문을 열었을 때는 따로 센다.
        mistake+=1 
    else:
        if choice==final_choice: 
            stay+=1
            if final_choice==car: 
                stay_win+=1
        else:
            move+=1
            if final_choice==car : 
                move_win+=1
    p+=1
print(round(stay/p,4), round(move/p,4), round(mistake/p,4))
print(stay_win/stay, move_win/move)
```
