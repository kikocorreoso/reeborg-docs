4번째 규칙
=============

앞선 수업에서, 최초 고안한 것보다 더 많은 상황에서 동작하는 프로그램을 설계했다. (동작하지 않는 다른 상황을 제안할 수 있지만, 연습문제로 충분히 했다.)
잊기 전에, 작성한 프로그램은 리보그가 벽을 따라 세상을 한번 탐색하도록 작성되었다. 프로그램이 다소 짧아 구조가 명확하게 보일 수 있지만, 처음으로 프로그램을 읽는 사람에게는 명확하게 보이지 않을 수 있다. 주석을 추가하든지 좀더 의미가 있는 단어를 사용하는 것이 좋은 생각이 된다. 생각하는 것 보다 다소 단어나 말이 길어지는 것처럼 보일 수 있지만, 주석을 추가해 시작해 봅시다::

    # 토큰을 내려 놓는 것으로 시작점을 표시한다.
    put()

    # 막히지 않는 방향을 찾아 이동을 시작한다.
    while not front_is_clear():
        turn_left()
    move()

    '''  토큰을 내려 놓은 장소로 돌아갔을 때,
    세상을 돌아 다닌 것을 알게 된다. ''''

    while not object_here():
        if right_is_clear():  # 우측 방향으로 돈다.
            turn_right()
            move()
        elif front_is_clear():    # 이동 ... 오른쪽 벽을 따라
            move()
        else:
            turn_left()  # 왼쪽으로 돌아 벽을 따라간다

이런 유형 방법이 각 명령문에 대한 의도를 명확히 하지만, 문제를 해결하는데 사용되는 *알고리즘(Algorithm)* 으로 알려진 방법을 요약하는 데는 그다지 도움이 되지 않는다. 따라서, 이렇게 주석을 다는 것은 여러분이 희망하는 다른 프로그램을 읽는 분들에게는 도움이 되지 않을지도 모른다. 주석을 읽으면, 작성된 프로그램이 두 개의 부분으로 구성된 것을 주목한다.

#. 첫 시작 지점을 표시한다.
#. 처음 시작 지점으로 돌아올때까지 오른쪽 벽을 따라 계속 이동한다.

프로그램을 다시 작성해서, 두 부분이 좀더 명확해 지도록 주석을 다르게 작성한다::

    ''' 이 프로그램은 리보그가 반시계 방향으로 벽을 따라 돌아
        처음 시작한 지점으로 다시 돌아와서 멈추는 프로그램입니다. '''

    def mark_starting_point_and_move():
        put()
        while not front_is_clear():
            turn_left()
        move()

    def follow_right_wall():
        if right_is_clear():
            turn_right()
            move()
        elif front_is_clear():
            move()
        else:
            turn_left()

    found_starting_point = object_here

    #######
    ##  함수 명령문 정의 끝; 아래 프로그램 실행.
    #######

    mark_starting_point_and_move()

    while not found_starting_point():
        follow_right_wall()

이것이 좀더 명확하지 않습니까?

**주의: 라이브러리에 ``follow_right_wall()`` 함수를 복사해 넣어 다시 필요할 때 사용할 수 있게 한다.**

결론
----------

해결할 수 있는 간단한 문제(직사각형 세상을 따라 돌아다님)에서 출발했고, 조금씩 조금씩 개선해서(*단계적 정제(stepwise refinement)* 라고도 부름), 다른 많은 문제를 해결하는데 사용할 수 있는 프로그램을 작성하게 되었다. 각 단계에서 변경사항을 적게하고, 더 복잡한 문제를 고려하기 전에, 확실히 동작하는 해법이 되는지 확인한다. 프로그램을 읽기 쉽고, 이해하기 쉽게 만드는 *알고리즘* 부분에 좀더 서술적인 명칭을 사용하기도 했다. 이것이 본인 자신의 프로그램을 작성할 때 사용해야 되는 전략이다:

.. index:: 4번째 규칙

.. important::

    **규칙 # 4**
        프로그램을 작성할 때 지킬 절차:

        #. 간단하고, 작게 시작합니다
        #. 한번에 작은 수정사항, 변경을 합니다.
        #. 각 단계의 수정 변경 사항이 전에 작성한 것과 잘 작동하는지 확인하세요.
        #. 각 명령문이 수행하는 것을 단순 반복하지 않는 적절한 주석을 추가하세요.
        #. 서술적인 이름을 사용하세요.

마지막 두 부분은 본질적으로 규칙 # 2와 같다.

이제, 다음 수업으로 이동하기 전에, 편집기에서 동작하는 프로그램인지 확인한다.

