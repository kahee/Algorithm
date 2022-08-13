{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "f1511e0e",
   "metadata": {},
   "source": [
    "# 10871 "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "id": "528f9bc2",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "10 5\n",
      "1 10 4 9 2 3 8 5 7 6\n"
     ]
    }
   ],
   "source": [
    "n, x = input().split()\n",
    "nums = input()\n",
    "nums = [i for i in nums.split(' ') if int(i) < int(x)]\n",
    "print(' '.join(nums))"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "5a0cd2ad",
   "metadata": {},
   "source": [
    "## 다른 사람이 짠 코드"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 41,
   "id": "15ecfdeb",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "10 5\n",
      "1 10 4 9 2 3 8 5 7 6\n",
      "1 4 2 3\n"
     ]
    }
   ],
   "source": [
    "a,b = map(int,input().split())\n",
    "score = [x for x in input().split() if int(x)<b]\n",
    "print(' '.join(score))"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "0496358e",
   "metadata": {},
   "source": [
    "## 2753"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 53,
   "id": "be964719",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "1999\n",
      "0\n"
     ]
    }
   ],
   "source": [
    "year = int(input())\n",
    "if year % 4 == 0 and (year % 100 != 0 or year % 400 == 0):\n",
    "    print(1)\n",
    "else:\n",
    "    print(0)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "1ed182fd",
   "metadata": {},
   "source": [
    "## 2490 - 윷놀이"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 73,
   "id": "8e84aaa5",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0 1 0 1\n",
      "B\n",
      "1 1 1 0\n",
      "A\n",
      "0 0 1 1\n",
      "B\n"
     ]
    }
   ],
   "source": [
    "for i in range(3):\n",
    "    play_list = [x for x in map(int,input().split())]\n",
    "\n",
    "    if sum(play_list) == 3:\n",
    "        print('A')\n",
    "    elif sum(play_list) == 2:\n",
    "        print('B')\n",
    "    elif sum(play_list) == 1:\n",
    "        print('C')\n",
    "    elif sum(play_list) == 0:\n",
    "        print('D')\n",
    "    elif sum(play_list) == 4:\n",
    "        print('E')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 67,
   "id": "3e267416",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "B\n",
      "A\n",
      "B\n"
     ]
    }
   ],
   "source": [
    "import sys\n",
    "# 도는 A, 개는 B, 걸은 C, 윷은 D, 모는 E로 \n",
    "for line in sys.stdin:\n",
    "    cnt = list(map(int, line.split())).count(0)\n",
    "    if cnt == 1:\n",
    "        print('A')\n",
    "    elif cnt == 2:\n",
    "        print('B')\n",
    "    elif cnt == 3:\n",
    "        print('C')\n",
    "    elif cnt == 4:\n",
    "        print('D')\n",
    "    elif cnt == 0:\n",
    "        print('E')"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.8"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
