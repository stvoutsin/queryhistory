# queryhistory

Python library for providing UWS job history using the async jobs endpoint
Allows querying by various filters, some which are run on the server side and are part of the UWS specification (last, filter by date) while custom filters can also be defined which are run on the client side.

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
