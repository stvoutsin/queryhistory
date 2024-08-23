# queryhistory
Python lib for providing UWS job History using the async jobs endpoint

## Installation
    pip install .

## Example Usage

    # Show 2 of my queries
    queries = query_history.get_queries(limit=2)
    print(queries)

    # Show my 5 most recent queries
    queries = query_history.get_queries(last=5)
    print(queries)

    # Show 10 most recent queries run after August 20th 2024
    queries = query_history.get_queries(after=datetime(2024, 8, 20), last=5)
    print(queries)

    # Custom job Filters
    filters = [
        lambda q: q.owner_id == "username",
        lambda q: q.phase == "COMPLETED"
    ]
    queries = query_history.get_queries(limit=10, recent=True, filters=filters)
