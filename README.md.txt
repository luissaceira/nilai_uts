# futsal_tournament_brochure.py

from datetime import datetime

class Team:
    def _init_(self, name: str, players: list[str]):
        self.name = name
        self.players = players

class Match:
    def _init_(self, team1: Team, team2: Team, date: str, time: str, venue: str):
        self.team1 = team1
        self.team2 = team2
        self.date = datetime.strptime(date, "%Y-%m-%d")
        self.time = datetime.strptime(time, "%I:%M %p")
        self.venue = venue

class Tournament:
    DATE_FORMAT = "%Y-%m-%d"
    TIME_FORMAT = "%I:%M %p"

    def _init_(self, name: str, teams: list[Team], matches: list[Match]):
        self.name = name
        self.teams = teams
        self.matches = matches

    def print_schedule(self) -> None:
        print(f"Tournament Schedule: {self.name}")
        print("-------------------------------")
        for match in self.matches:
            print(f"{match.team1.name} vs {match.team2.name} on {match.date.strftime(self.DATE_FORMAT)} at {match.time.strftime(self.TIME_FORMAT)} at {match.venue}")
        print("-------------------------------")

    def print_teams(self) -> None:
        print(f"Tournament Teams: {self.name}")
        print("-------------------------------")
        for team in self.teams:
            print(f"{team.name}: {', '.join(team.players)}")
        print("-------------------------------")

# Create teams
team_a = Team("Team A", ["Player 1", "Player 2", "Player 3"])
team_b = Team("Team B", ["Player 4", "Player 5", "Player 6"])
team_c = Team("Team C", ["Player 7", "Player 8", "Player 9"])

# Create matches
match1 = Match(team_a, team_b, "2024-05-17", "10:00 AM", "Court 1")
match2 = Match(team_b, team_c, "2024-05-18", "2:00 PM", "Court 2")
match3 = Match(team_a, team_c, "2024-05-19", "4:00 PM", "Court 3")

# Create tournament
tournament = Tournament("Futsal Tournament 2024", [team_a, team_b, team_c], [match1, match2, match3])

# Print schedule and teams
tournament.print_schedule()
tournament.print_teams()