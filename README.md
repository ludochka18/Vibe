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

    sorted_weights = sorted(weights)
    
    light_index = 0
    heavy_index = len(sorted_weights) - 1
    platforms_count = 0
    
    while light_index <= heavy_index:
        # Пытаемся посадить на одну платформу самого тяжелого и самого легкого
        if sorted_weights[light_index] + sorted_weights[heavy_index] <= limit:
            light_index += 1
        
        # Самый тяжелый робот всегда занимает платформу
        heavy_index -= 1
        platforms_count += 1

    return platforms_count


if __name__ == "__main__":
    # Чтение входных данных
    weights = [int(num) for num in input().strip().split()]
    limit = int(input().strip())
    
    # Вычисление результата
    result = min_platforms(weights, limit)
    
    # Вывод результата
    print(result)
