from typing import List

def min_platforms(weights: List[int], limit: int) -> int:
    """
    Определяет минимальное количество платформ для перевозки роботов.
    
    Args:
        weights: список весов роботов
        limit: максимальный вес на одной платформе
        
    Returns:
        минимальное количество платформ
    """
    # Сортируем веса по возрастанию
    weights.sort()
    
    left = 0  # указатель на самого легкого робота
    right = len(weights) - 1  # указатель на самого тяжелого робота
    platforms = 0
    
    while left <= right:
        # Пытаемся посадить на одну платформу самого тяжелого и самого легкого
        if weights[left] + weights[right] <= limit:
            # Можем перевезти двоих
            left += 1
            right -= 1
        else:
            # Можем перевезти только тяжелого
            right -= 1
        
        platforms += 1
    
    return platforms


if __name__ == "__main__":
    # Чтение входных данных
    weights = list(map(int, input().strip().split()))
    limit = int(input().strip())
    
    # Вычисление результата
    result = min_platforms(weights, limit)
    
    # Вывод результата
    print(result)
